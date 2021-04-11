<template>
  <div class="hello">
    税前税后工资收入变化表格
    <div id="chartWrapper">
    </div>
  </div>
</template>

<script>
import * as echarts from 'echarts'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted() {
    // 基于准备好的dom，初始化echarts实例
    let myChart = echarts.init(document.getElementById('chartWrapper'));



    //-----------------------------dn：可进行参数设置------------------------------
    var bFixedIn = false;           // 固定社保基数标志：false不固定，true固定
    var bFixedHouse = false;        // 固定公积金基数标志：false不固定，true固定

    var fFixedInBase = 13768;       // 固定的社保基数
    var fFixedHouseBase = 12000;     // 固定的公积金基数

    var fExemptionPoint = 5000;     // 免税起点

// 五险一金个人比例
    var fRateInEnd = 0.08;          // 养老 8%
    var fRateInMed = 0.02;          // 医疗 2%
    var fRateInUnEmp = 0.002;       // 失业 0.2%
    var fRateInInjuery = 0;         // 工伤
    var fRateInMate = 0;            // 生育
    var fRateInHouse = 0.05;        // 公积金

// 北京2016年上、下限

    // var fInEndMin = 2834;           // 养老保险下限
    // var fInEndMax = 21258;          // 养老保险上限
    //
    // var fInMedMin = 4252;           // 医疗保险下限
    // var fInMedMax = fInEndMax;      // 医疗保险上限
    //
    // var fInHouseMin = 412.8 / 2;    // 公积金下限
    // var fInHouseMax = 5101.92 / 2;  // 公积金上限

// 杭州2021年上、下限
    var fInEndMin = 3321.6;           // 养老保险下限
    var fInEndMax = 16608;          // 养老保险上限

    var fInMedMin = 3321.6;           // 医疗保险下限
    var fInMedMax = 16608;      // 医疗保险上限

    var fInHouseMin = 2010 * 0.05;    // 公积金下限
    var fInHouseMax = 29335 * 0.12;  // 公积金上限

//-----------------------------up：可进行参数设置------------------------------

// 计算人个交五险一金
    function funcCalc5In(fIncome) {
      var fSum = 0;

      // 养老
      var fInEndTmp = fIncome < fInEndMin ? fInEndMin
          : (fIncome > fInEndMax ? fInEndMax : fIncome);
      fSum += fInEndTmp * fRateInEnd;

      // 医疗
      var fInMedTmp = fIncome < fInMedMin ? fInMedMin
          : (fIncome > fInMedMax ? fInMedMax : fIncome);
      fSum += fInMedTmp * fRateInMed;

      // 失业
      var fInUnEmpTmp = fIncome < fInEndMin ? fInEndMin
          : (fIncome > fInEndMax ? fInEndMax : fIncome);
      fSum += fInUnEmpTmp * fRateInUnEmp;

      // 工伤
      var fInInjueryTmp = fIncome < fInMedMin ? fInMedMin
          : (fIncome > fInMedMax ? fInMedMax : fIncome);
      fSum += fInInjueryTmp * fRateInInjuery;

      // 生育
      var fInMateTmp = fIncome < fInMedMin ? fInMedMin
          : (fIncome > fInMedMax ? fInMedMax : fIncome);
      fSum += fInMateTmp * fRateInMate;

      return fSum;
    }

// 计算公积金
    function funcCalcHouse(fIncome) {
      // 公积金
      var fInHouseTmp = fIncome < 10000 ? fIncome * fRateInHouse : fIncome * 0.12;
      // var fInHouseTmp = fIncome * fRateInHouse;
      fInHouseTmp = fInHouseTmp < fInHouseMin ? fInHouseMin
          : (fInHouseTmp > fInHouseMax ? fInHouseMax : fInHouseTmp);

      return fInHouseTmp;
    }

// 计算税
    function funcCalcTax(fIncome, f5In, fExemptionPoint) {
      var iRet = 0;
      var strRank = '';

      var fVal = fIncome - f5In - fExemptionPoint;
      if (fVal <= 0) {
        iRet = 0;
        strRank = '不用交税';
      }
      else if (fVal <= 3000){
        iRet = fVal * 0.03;
        strRank = '(0, 3000]';
      }
      else if (fVal <= 12000) {
        iRet = fVal * 0.1 - 210;
        strRank = '(3000, 12000]';
      }
      else if (fVal <= 25000) {
        iRet = fVal * 0.2 - 1410;
        strRank = '(12000, 25000]';
      }
      else if (fVal <= 35000) {
        iRet = fVal * 0.25 - 2660;
        strRank = '(25000, 35000]';
      }
      else if (fVal <= 55000) {
        iRet = fVal * 0.3 - 4410;
        strRank = '(35000, 55000]';
      }
      else if (fVal <= 80000) {
        iRet = fVal * 0.35 - 7160;
        strRank = '(55000, 80000]';
      }
      else {
        iRet = fVal * 0.45 - 15160;
        strRank = '土豪';
      }
      var objTmp = {};
      objTmp.val = iRet;
      objTmp.rank = strRank;
      return objTmp;
    }

    var aryIncomeX = [];
    var aryIncomeYTax = [];
    var aryIncomeY = [];
    var aryIncomeYRankDesc = [];
    var aryIncomeY5In = [];
    var aryIncomeYHouse = [];
    var fIncomeLeft = 2000;
    var fIncomeRight = 90000;
    for (var i = fIncomeLeft; i <= fIncomeRight; i += 100) {
      aryIncomeX.push(i);
      var f5In = funcCalc5In(bFixedIn ? fFixedInBase : i); //.toFixed(2);
      var fHousePerson = funcCalcHouse(bFixedHouse ? fFixedHouseBase : i); //.toFixed(2);
      var f5In_House = f5In + fHousePerson;
      var objVal_Rank = funcCalcTax(i, f5In_House, fExemptionPoint);
      var fTax = Math.ceil(objVal_Rank.val);

      aryIncomeYTax.push(fTax);
      aryIncomeY.push(i - fTax - f5In_House);
      aryIncomeY5In.push(f5In);
      aryIncomeYHouse.push(fHousePerson);
      aryIncomeYRankDesc.push(objVal_Rank.rank);
    }

    myChart.setOption({
      title: {
        text: '杭州工资税负表 个税起征点 : ' + fExemptionPoint
      },
      tooltip: {
        trigger: 'axis',
        formatter: function(params) {
          var iIndex = params[0].dataIndex;
          var aryHtml = [];

          // 收入
          aryHtml.push('收入：' + aryIncomeX[iIndex] + '<br />');

          // 五险
          aryHtml.push('五险：' + aryIncomeY5In[iIndex].toFixed(2) + '<br />');

          // 公积金
          aryHtml.push('公积金：' + aryIncomeYHouse[iIndex].toFixed(2) + '<br />');

          // 五险+公积金
          aryHtml.push('五险+公积金：' + (aryIncomeY5In[iIndex] + aryIncomeYHouse[iIndex]).toFixed(2) + '<br />');

          // 个税
          aryHtml.push('个税：' + aryIncomeYTax[iIndex].toFixed(2) + '<br />');

          // 个税等级
          aryHtml.push('个税等级：' + aryIncomeYRankDesc[iIndex] + '<br />');

          // 五险+公积金+个税
          aryHtml.push('五险+公积金+个税：' + (aryIncomeY5In[iIndex] + aryIncomeYHouse[iIndex] + aryIncomeYTax[iIndex]).toFixed(2) + '<br />');

          // 税后收入
          aryHtml.push('税后收入：' + aryIncomeY[iIndex].toFixed(2) + '<br />');

          // +公积金税后收入
          aryHtml.push('+公积金税后收入：' + (aryIncomeY[iIndex] + aryIncomeYHouse[iIndex] * 2).toFixed(2) + '<br />');

          // 年收入
          aryHtml.push('年收入：' + (aryIncomeX[iIndex] * 12).toFixed(2) + '<br />');

          // 税后年收入
          aryHtml.push('税后年收入：' + (aryIncomeY[iIndex] * 12).toFixed(2) + '<br />');

          // +公积金税后年收入
          aryHtml.push('+公积金税后年收入：' + ((aryIncomeY[iIndex] + aryIncomeYHouse[iIndex] * 2) * 12).toFixed(2) + '<br />');

          // 年缴税
          aryHtml.push('年缴税：' + (aryIncomeYTax[iIndex] * 12).toFixed(2) + '<br />');

          return aryHtml.join('');
        }
      },
      xAxis: {
        data: aryIncomeX
      },
      yAxis: [
        {
          type: 'value',
          scale: true,
          name: 'tax',
          //max: 20000,
          min: 0
        },
        {
          type: 'value',
          scale: true,
          name: 'income',
          max: fIncomeRight,
          min: 0,
          splitLine: {
            show: false
          }
        }
      ],
      legend: {
        right: 20,
        data: ['tax', 'income'],
        formatter(name) {
          if (name === 'tax') {
            return '缴税额'
          } else {
            return '税后月收入'
          }
        }
      },
      dataZoom: [{
        start: 0,
        end: 100
      }, {
        type: 'inside'
      }],

      series: [{
        name: 'tax',
        type: 'line',
        yAxisIndex: 0,
        data: aryIncomeYTax
      }
        ,
        {
          name: 'income',
          type: 'line',
          yAxisIndex: 1,
          data: aryIncomeY
        }
      ]
    });
  }
}
</script>

<style scoped>
#chartWrapper{
  width: 500px;
  height: 300px;
  margin: 200px auto;
}
</style>
