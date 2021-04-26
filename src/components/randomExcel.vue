<template>
  <div class="hello">
    身高正态分布表格
    <div id="heightWrapper"></div>
    颜值正态分布表格
    <div id="yanzhiWrapper"></div>
    皮囊正态分布表格
    <div id="bodyWrapper"></div>
    灵魂正态分布表格
    <div id="soulWrapper"></div>
    财富指数分布表格
    <div id="weightWrapper"></div>
  </div>
</template>

<script>
// import * as echarts from 'echarts'
export default {
  name: 'mameryExcel',
  data() {
    return {

    }
  },
  created() {
    let manObj = {}
    let womanObj = {}
    for (let i = 0; i < 10000; i++) {
      const gotManValue = Math.floor(this.getNumberInNormalDistribution1(172, 10))
      const gotWomanValue = Math.floor(this.getNumberInNormalDistribution1(158, 10))
      if (!Object.prototype.hasOwnProperty.call(manObj, gotManValue)) {
        manObj[gotManValue] = 1
      } else {
        manObj[gotManValue]++
      }

      if (!Object.prototype.hasOwnProperty.call(womanObj, gotWomanValue)) {
        womanObj[gotWomanValue] = 1
      } else {
        womanObj[gotWomanValue]++
      }
    }
    console.log(manObj, womanObj)

    // let myChart = echarts.init(document.getElementById('heightWrapper'));
    // console.log(myChart)
    // myChart.setOption({
    //   title: {
    //     text: '身高正态分布表格'
    //   },
    //   tooltip: {
    //     target: 'axios'
    //   },
    //   xAxis: {
    //     data: []
    //   },
    //   yAxis: [
    //     {
    //       type: 'value',
    //       scale: true,
    //       name: 'man'
    //     },
    //     {
    //       type: 'value',
    //       scale: true,
    //       name: 'woman'
    //     },
    //   ]
    // })
  },
  methods: {
    getNumberInNormalDistribution(mean, std_dev) {
      return mean + (this.randomNormalDistribution() * std_dev);
    },

    randomNormalDistribution() {
      var u = 0.0, v = 0.0, w = 0.0, c = 0.0;
      do {
        //获得两个（-1,1）的独立随机变量
        u = Math.random() * 2 - 1.0;
        v = Math.random() * 2 - 1.0;
        w = u * u + v * v;
      } while (w == 0.0 || w >= 1.0)
      //这里就是 Box-Muller转换
      c = Math.sqrt((-2 * Math.log(w)) / w);
      //返回2个标准正态分布的随机数，封装进一个数组返回
      //当然，因为这个函数运行较快，也可以扔掉一个
      //return [u*c,v*c];
      return u * c;
    },

    getNumberInNormalDistribution1(mean, std_dev) {
      return mean + (this.uniform2NormalDistribution() * std_dev);
    },

    uniform2NormalDistribution() {
      var sum = 0.0;
      for (var i = 0; i < 12; i++) {
        sum = sum + Math.random();
      }
      return sum - 6.0;
    }

  }
}
</script>

<style scoped>
#heightWrapper,
#yanzhiWrapper,
#bodyWrapper,
#soulWrapper,
#weightWrapper {
  width: 500px;
  height: 300px;
  margin: 100px auto 0;
}
</style>
