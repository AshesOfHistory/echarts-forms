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
      // manObj: {
      //   2: 5,
      //   3: 3,
      //   4: 3,
      //   5: 6,
      //   6: 4,
      //   7: 4,
      //   8: 1,
      //   9: 11,
      //   10: 4,
      //   11: 9,
      //   12: 14,
      //   13: 19,
      //   14: 24,
      //   15: 18,
      //   16: 31,
      //   17: 21,
      //   18: 24,
      //   19: 33,
      //   20: 35,
      //   21: 49,
      //   22: 50,
      //   23: 56,
      //   24: 51,
      //   25: 71,
      //   26: 67,
      //   27: 82,
      //   28: 86,
      //   29: 104,
      //   30: 121,
      //   31: 135,
      //   32: 150,
      //   33: 163,
      //   34: 161,
      //   35: 163,
      //   36: 186,
      //   37: 205,
      //   38: 204,
      //   39: 193,
      //   40: 205,
      //   41: 226,
      //   42: 213,
      //   43: 248,
      //   44: 233,
      //   45: 299,
      //   46: 239,
      //   47: 246,
      //   48: 244,
      //   49: 257,
      //   50: 289,
      //   51: 253,
      //   52: 272,
      //   53: 249,
      //   54: 250,
      //   55: 224,
      //   56: 251,
      //   57: 236,
      //   58: 222,
      //   59: 220,
      //   60: 197,
      //   61: 220,
      //   62: 198,
      //   63: 197,
      //   64: 142,
      //   65: 166,
      //   66: 138,
      //   67: 133,
      //   68: 135,
      //   69: 112,
      //   70: 97,
      //   71: 104,
      //   72: 96,
      //   73: 81,
      //   74: 83,
      //   75: 69,
      //   76: 49,
      //   77: 41,
      //   78: 40,
      //   79: 32,
      //   80: 30,
      //   81: 36,
      //   82: 28,
      //   83: 21,
      //   84: 13,
      //   85: 21,
      //   86: 14,
      //   87: 15,
      //   88: 13,
      //   89: 4,
      //   90: 5,
      //   91: 9,
      //   92: 4,
      //   93: 3,
      //   94: 1,
      //   95: 4,
      //   96: 1,
      //   98: 2,
      //   103: 1,
      //   104: 2,
      //   0: 1
      // },
      // womenObj: {
      //   3: 1,
      //   4: 4,
      //   5: 1,
      //   6: 4,
      //   7: 3,
      //   8: 4,
      //   9: 8,
      //   10: 7,
      //   11: 13,
      //   12: 10,
      //   13: 15,
      //   14: 17,
      //   15: 21,
      //   16: 24,
      //   17: 25,
      //   18: 29,
      //   19: 34,
      //   20: 37,
      //   21: 44,
      //   22: 54,
      //   23: 49,
      //   24: 60,
      //   25: 76,
      //   26: 83,
      //   27: 74,
      //   28: 94,
      //   29: 79,
      //   30: 112,
      //   31: 136,
      //   32: 150,
      //   33: 143,
      //   34: 148,
      //   35: 168,
      //   36: 187,
      //   37: 198,
      //   38: 215,
      //   39: 211,
      //   40: 219,
      //   41: 222,
      //   42: 232,
      //   43: 237,
      //   44: 264,
      //   45: 270,
      //   46: 254,
      //   47: 269,
      //   48: 269,
      //   49: 256,
      //   50: 272,
      //   51: 294,
      //   52: 271,
      //   53: 243,
      //   54: 265,
      //   55: 215,
      //   56: 223,
      //   57: 227,
      //   58: 205,
      //   59: 216,
      //   60: 231,
      //   61: 199,
      //   62: 204,
      //   63: 178,
      //   64: 154,
      //   65: 161,
      //   66: 145,
      //   67: 122,
      //   68: 122,
      //   69: 119,
      //   70: 118,
      //   71: 76,
      //   72: 81,
      //   73: 73,
      //   74: 67,
      //   75: 64,
      //   76: 51,
      //   77: 53,
      //   78: 52,
      //   79: 46,
      //   80: 27,
      //   81: 27,
      //   82: 30,
      //   83: 19,
      //   84: 21,
      //   85: 21,
      //   86: 17,
      //   87: 13,
      //   88: 12,
      //   89: 6,
      //   90: 9,
      //   91: 3,
      //   92: 2,
      //   93: 4,
      //   94: 2,
      //   98: 1,
      //   99: 2,
      //   100: 2,
      //   101: 1,
      //   104: 1,
      //   0: 3
      // },

      manObj: {
        1: 1,
        6: 3,
        7: 3,
        8: 3,
        9: 2,
        10: 2,
        11: 2,
        12: 1,
        13: 4,
        14: 5,
        15: 10,
        16: 12,
        17: 12,
        18: 19,
        19: 13,
        20: 16,
        21: 23,
        22: 24,
        23: 32,
        24: 36,
        25: 31,
        26: 43,
        27: 57,
        28: 56,
        29: 55,
        30: 77,
        31: 66,
        32: 96,
        33: 98,
        34: 100,
        35: 111,
        36: 135,
        37: 149,
        38: 138,
        39: 129,
        40: 170,
        41: 164,
        42: 157,
        43: 185,
        44: 202,
        45: 227,
        46: 247,
        47: 196,
        48: 251,
        49: 266,
        50: 250,
        51: 262,
        52: 257,
        53: 287,
        54: 259,
        55: 260,
        56: 246,
        57: 273,
        58: 267,
        59: 257,
        60: 263,
        61: 231,
        62: 226,
        63: 252,
        64: 200,
        65: 191,
        66: 188,
        67: 195,
        68: 195,
        69: 160,
        70: 158,
        71: 148,
        72: 151,
        73: 138,
        74: 128,
        75: 92,
        76: 95,
        77: 88,
        78: 81,
        79: 57,
        80: 63,
        81: 60,
        82: 56,
        83: 51,
        84: 34,
        85: 37,
        86: 37,
        87: 32,
        88: 20,
        89: 30,
        90: 23,
        91: 9,
        92: 9,
        93: 10,
        94: 7,
        95: 10,
        96: 6,
        97: 7,
        98: 5,
        99: 1,
        100: 2,
        101: 3,
        102: 3,
        105: 1
      },// 55
      womenObj: {
        4: 1,
        9: 1,
        12: 1,
        16: 2,
        17: 1,
        18: 4,
        19: 2,
        20: 2,
        21: 5,
        22: 6,
        23: 6,
        24: 7,
        25: 5,
        26: 10,
        27: 6,
        28: 11,
        29: 13,
        30: 26,
        31: 14,
        32: 20,
        33: 27,
        34: 33,
        35: 33,
        36: 45,
        37: 52,
        38: 68,
        39: 80,
        40: 81,
        41: 81,
        42: 96,
        43: 71,
        44: 90,
        45: 136,
        46: 124,
        47: 121,
        48: 148,
        49: 158,
        50: 162,
        51: 195,
        52: 180,
        53: 199,
        54: 215,
        55: 239,
        56: 218,
        57: 245,
        58: 247,
        59: 261,
        60: 243,
        61: 256,
        62: 278,
        63: 231,
        64: 242,
        65: 270,
        66: 258,
        67: 269,
        68: 244,
        69: 252,
        70: 249,
        71: 229,
        72: 264,
        73: 224,
        74: 223,
        75: 224,
        76: 178,
        77: 216,
        78: 173,
        79: 171,
        80: 147,
        81: 146,
        82: 142,
        83: 123,
        84: 107,
        85: 99,
        86: 96,
        87: 72,
        88: 84,
        89: 72,
        90: 64,
        91: 69,
        92: 52,
        93: 42,
        94: 39,
        95: 41,
        96: 27,
        97: 22,
        98: 22,
        99: 13,
        100: 12,
        101: 6,
        102: 11,
        103: 12,
        104: 7,
        105: 10,
        106: 4,
        107: 6,
        108: 2,
        109: 2,
        110: 2,
        111: 1,
        112: 3,
        113: 1
      },// 65
      middleManNum: 0,
      middleHeightManNum: 0,
      highManNum: 0,
      middleWomanNum: 0,
      middleHeightWomanNum: 0,
      highWomanNum: 0
    }
  },
  created() {
    // let manObj = {}
    // let womanObj = {}
    // for (let i = 0; i < 10000; i++) {
    //   // const gotManValue = Math.floor(this.getNumberInNormalDistribution1(172, 10))
    //   // const gotWomanValue = Math.floor(this.getNumberInNormalDistribution1(158, 10))
    //
    //   const gotManValue = Math.floor(this.getNumberInNormalDistribution1(50, 15))
    //   const gotWomanValue = Math.floor(this.getNumberInNormalDistribution1(50, 15))
    //   if (!Object.prototype.hasOwnProperty.call(manObj, gotManValue)) {
    //     manObj[gotManValue] = 1
    //   } else {
    //     manObj[gotManValue]++
    //   }
    //
    //   if (!Object.prototype.hasOwnProperty.call(womanObj, gotWomanValue)) {
    //     womanObj[gotWomanValue] = 1
    //   } else {
    //     womanObj[gotWomanValue]++
    //   }
    // }
    // console.log(manObj, womanObj)
    console.log('男性素颜分值分布情况:', this.manObj, '女性素颜分值分布情况', this.womenObj)

    let middleManNum = 0;
    let middleHeightManNum = 0;
    let highManNum = 0;
    let middleWomanNum = 0;
    let middleHeightWomanNum = 0;
    let highWomanNum = 0;
    for (let faceValue in this.manObj) {
      if (faceValue >= 60 && faceValue < 75 ) {
        middleManNum += this.manObj[faceValue]
      } else if (faceValue >= 75 && faceValue < 90) {
        middleHeightManNum += this.manObj[faceValue]
      } else if (faceValue >= 90) {
        highManNum += this.manObj[faceValue]
      }
      this.randomedFaceValue('man', faceValue, this.manObj[faceValue])
    }
    console.log('素颜中等男性', middleManNum, middleManNum / 100+'%', '素颜中上男性', middleHeightManNum, middleHeightManNum / 100+'%','素颜上男性', highManNum, highManNum / 100+'%')
    console.log('真实中等男性', this.middleManNum, this.middleManNum / 100+'%','真实中上男性', this.middleHeightManNum, this.middleHeightManNum / 100+'%','真实上男性', this.highManNum, this.highManNum / 100+'%')
    for (let faceValue in this.womenObj) {
      if (faceValue >= 60 && faceValue < 75 ) {
        middleWomanNum += this.womenObj[faceValue]
      } else if (faceValue >= 75 && faceValue < 90) {
        middleHeightWomanNum += this.womenObj[faceValue]
      } else if (faceValue >= 90) {
        highWomanNum += this.womenObj[faceValue]
      }
      this.randomedFaceValue('woman', faceValue, this.womenObj[faceValue])
    }
    console.log('素颜中等女性',middleWomanNum, middleWomanNum / 100+'%','素颜中上女性', middleHeightWomanNum, middleHeightWomanNum / 100+'%','素颜上女性', highWomanNum, highWomanNum / 100+'%')
    console.log('真实中等女性',this.middleWomanNum, this.middleWomanNum / 100+'%','真实中上女性', this.middleHeightWomanNum, this.middleHeightWomanNum / 100+'%','真实上女性', this.highWomanNum, this.highWomanNum / 100+'%')

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
    },
    randomedFaceValue(sex, faceValue, number) {
      faceValue = Number(faceValue)
      if (sex === 'man') {
        for (let i = 0; i < number; i++) {
          const random = Math.random()
          let gotFaceValue, randomValue
          if (random <= 0.3) {
            randomValue = Math.round(Math.random()*10)
            gotFaceValue = faceValue + randomValue
          } else {
            randomValue = Math.round(Math.random()*10)
            gotFaceValue = faceValue - randomValue
          }
          // console.log(faceValue, gotFaceValue, randomValue)
          if (gotFaceValue >= 60 && gotFaceValue < 75) {
            this.middleManNum++
          } else if (gotFaceValue >= 75 && gotFaceValue < 90) {
            this.middleHeightManNum++
          } else if (gotFaceValue >= 90) {
            this.highManNum++
          }
        }
      } else {
        for (let i = 0; i < number; i++) {
          const random = Math.random()
          let gotFaceValue, randomValue
          if (random <= 0.3) {
            randomValue = Math.round(Math.random()*5)
            gotFaceValue = faceValue - randomValue
          } else {
            randomValue = Math.round(Math.random()*15)
            gotFaceValue = faceValue + randomValue
          }
          // console.log(faceValue, gotFaceValue, randomValue)
          if (gotFaceValue >= 60 && gotFaceValue < 75) {
            this.middleWomanNum++
          } else if (gotFaceValue >= 75 && gotFaceValue < 90) {
            this.middleHeightWomanNum++
          } else if (gotFaceValue >= 90) {
            this.highWomanNum++
          }
        }
      }
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
