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
    // 本文在银河统计Web Service接口基础上，编制JS类函数生成常用分布随机数，为在网页中实现模拟仿真项目提供方便。
    // var webTJ1 = {

    // }
    // var oURL = webTJ1.wsFC.getURL("normal_r", 100, 4, 0, 1, 0); //获得生成正态分布随机数接口网址（均值为0、标准差为1）
    // webTJ1.wsFC.setRSample(oURL, 1); //将按指定oURL返回的随机数按数组格式赋值给系统变量webTJ1.wsRSArr1
    // webTJ1.wsFC.setRSample(oURL, 10); //将按指定oURL返回的随机数按数组格式赋值给系统变量webTJ1.wsRSArrs[0]
    // var oURL1 = webTJ1.wsFC.getURL("uniform_r", 100, 4, 1, 6, 0); //获得生成均匀分布随机数接口网址
    // webTJ1.wsFC.setRSample(oURL1, 2); //将按指定oURL返回的随机数按数组格式赋值给系统变量webTJ1.wsRSArr2
    // webTJ.display("生成随机数，并赋值给指定系统变量！", 0);
    // //注：根据设定的不同随机数接口变量oURL获取相应的随机数，并以数组格式赋值给指定系统变量，以备在“随机数运用代码”中调用。

    // webTJ.clear();
    // webTJ.display(webTJ1.wsRSArr1, 0);
    // webTJ.display(webTJ1.wsRSArrs[0], 0);
    // webTJ.display(webTJ1.wsRSArr2, 0);

    // 函数：webTJ1.wsFC.getURL(t,s,d,c1,c2,c3)
    // 功能：根据参数返回统计Web Service接口网址
    // 参数：参见getURL函数参数表（附表—1）
    // 函数getURL(t,s,d,c1,c2,c3)的参数和统计Web Service接口网址的对应关系为，t-type、s-sample_size、d-decimal_places、c1、c2、c3为各种分布的特有参数，c2、c3为*时分布无该参数。各分布特有参数取值参见统计随机数及临界值Web Service接口

    // 
  },
  methods: {


  }
}
</script>
