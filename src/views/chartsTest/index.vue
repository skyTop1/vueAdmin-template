<template>
  <div class="chartsTest">
    <el-row :gutter="12">
      <el-col :span="12">
        <el-card shadow="never">
          <div id="test1"></div>
          <div id="test2"></div>
          <div id="test5"></div>
        </el-card>
      </el-col>
      <el-col :span="12">
        <el-card shadow="never">
          <div id="test3"></div>
        </el-card>
      </el-col>
    </el-row>
    <el-card class="mt10"
             shadow="never">
      <div id="test4"></div>
    </el-card>
  </div>
</template>
<script>
import echarts from 'echarts'
var xAxisData = []
var data1 = []
var data2 = []
var data3 = []
var data4 = []

for (var i = 0; i < 10; i++) {
  xAxisData.push('Class' + i)
  data1.push((Math.random() * 2).toFixed(2))
  data2.push(-Math.random().toFixed(2))
  data3.push((Math.random() * 5).toFixed(2))
  data4.push((Math.random() + 0.3).toFixed(2))
}

var itemStyle = {
  normal: {
  },
  emphasis: {
    color: '#0094ff',
    barBorderWidth: 1,
    shadowBlur: 10,
    shadowOffsetX: 0,
    shadowOffsetY: 0,
    shadowColor: 'rgba(0,0,0,0.5)'
  }
}
export default {
  name: 'chartsTest',
  data() {
    return {
      chart: null,
      option1: {
        series: {
          type: 'pie',
          data: [
            { name: 'A', value: 1212 },
            { name: 'B', value: 2323 },
            { name: 'C', value: 1919 }
          ]
        }
      },
      option2: {
        title: {
          text: 'ECharts 入门示例'
        },
        tooltip: {},
        xAxis: {
          data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
        },
        yAxis: {},
        series: [{
          name: '销量',
          barWidth: '30%',
          type: 'bar',
          data: [5, 20, 36, 10, 10, 20]
        }]
      },
      option3: {
        series: [
          {
            name: '访问来源',
            type: 'pie',
            radius: ['50%', '70%'],
            data: [
              { value: 235, name: '视频广告' },
              { value: 274, name: '联盟广告' },
              { value: 310, name: '邮件营销' },
              { value: 335, name: '直接访问' },
              { value: 400, name: '搜索引擎' }
            ]
          }
        ]
      },
      option4: {
        backgroundColor: '#eee',
        // legend: {
        //   data: ['bar', 'bar2', 'bar3', 'bar4'],
        //   align: 'left',
        //   left: 10
        // },
        // brush: {
        //   toolbox: ['rect', 'polygon', 'lineX', 'lineY', 'keep', 'clear'],
        //   xAxisIndex: 0
        // },
        // toolbox: {
        //   feature: {
        //     magicType: {
        //       type: ['stack', 'tiled']
        //     },
        //     dataView: {}
        //   }
        // },
        tooltip: {},
        xAxis: {
          data: xAxisData,
          name: 'X Axis',
          silent: false,
          axisLine: { onZero: true },
          splitLine: { show: false },
          splitArea: { show: false }
        },
        yAxis: {
          inverse: true,
          splitArea: { show: false }
        },
        grid: {
          left: 100
        },
        // visualMap: {
        //   type: 'continuous',
        //   dimension: 1,
        //   text: ['High', 'Low'],
        //   inverse: true,
        //   itemHeight: 200,
        //   calculable: true,
        //   min: -2,
        //   max: 6,
        //   top: 60,
        //   left: 10,
        //   inRange: {
        //     colorLightness: [0.4, 0.8]
        //   },
        //   outOfRange: {
        //     color: '#bbb'
        //   },
        //   controller: {
        //     inRange: {
        //       color: '#2f4554'
        //     }
        //   }
        // },
        series: [
          {
            name: 'bar',
            type: 'bar',
            // stack: 'one1',
            itemStyle: itemStyle,
            data: data1
          },
          {
            name: 'bar2',
            type: 'bar',
            // stack: 'one',
            itemStyle: itemStyle,
            data: data2
          },
          {
            name: 'bar3',
            type: 'bar',
            // stack: 'two1',
            itemStyle: itemStyle,
            data: data3
          },
          {
            name: 'bar4',
            type: 'bar',
            // stack: 'two',
            itemStyle: itemStyle,
            data: data4
          }
        ]
      },
      option5: {
        color: ['#3398DB'],
        title: {
          text: '1001', // ${HunitID}
          show: false
        },
        tooltip: {
          // trigger: 'axis',
          // axisPointer: { // 坐标轴指示器，坐标轴触发有效
          //   type: 'shadow' // 默认为直线，可选为：'line' | 'shadow'
          // }
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        xAxis: [
          // {
          //   type: 'category',
          //   data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
          //   axisTick: {
          //     alignWithLabel: true
          //   }
          // }

          {
            splitLine: { show: false },
            type: 'category',
            data: ['社交人际', '沟通交流', '心理认知', '游戏玩耍嘻嘻嘻嘻嘻嘻', '大小运动', '生活自理', '执行管控', '知识常识'],
            splitArea: { show: false },
            axisLabel: {
              show: true,
              interval: 0,
              formatter: function(params) {
                var newParamsName = ''
                var paramsNameNumber = params.length
                var provideNumber = 20 // 一行显示几个字
                var rowNumber = Math.ceil(paramsNameNumber / provideNumber)
                if (paramsNameNumber > provideNumber) {
                  for (var p = 0; p < rowNumber; p++) {
                    var tempStr = ''
                    var start = p * provideNumber
                    var end = start + provideNumber
                    if (p === rowNumber - 1) {
                      tempStr = params.substring(start, paramsNameNumber)
                    } else {
                      tempStr = params.substring(start, end) + '\n'
                    }
                    newParamsName += tempStr
                  }
                } else {
                  newParamsName = params
                }
                return newParamsName
              },
              textStyle: {
                color: '#6861a6' // 文字颜色
              }
            }
          }
        ],
        yAxis: [{
          type: 'value'
        }],
        label: {
          normal: {
            show: true, // 显示数据
            position: 'top', // 显示数据位置 'top/right/left/insideLeft/insideRight/insideTop/insideBottom'
            color: '#999'
          }
        },
        series: [
          {
            name: '直接访问',
            type: 'bar',
            barGap: 0,
            barWidth: '40',
            data: [{ value: 11 }, { value: 22 }, { value: 333 }, { value: 22 }, { value: 41 }, { value: 54 }, { value: 64 }],
            itemStyle: {
            // color: p => p.dataIndex === curInt ? '#9BCA63' : '#FE8463',
              normal: {
                color: '#9BCA63'
              },
              emphasis: {
                color: '#FE8463',
                barBorderWidth: 1,
                shadowBlur: 10,
                shadowOffsetX: 0,
                shadowOffsetY: 0,
                shadowColor: 'rgba(0,0,0,0.5)'
              }
            }
          },
          {
            name: '直接访问',
            type: 'bar',
            barWidth: '40',
            data: [{ value: 11 }, { value: 22 }, { value: 333 }, { value: 22 }, { value: 41 }, { value: 54 }, { value: 64 }],
            itemStyle: {
            // color: p => p.dataIndex === curInt ? '#9BCA63' : '#FE8463',
              normal: {
                color: '#911111'
              },
              emphasis: {
                color: '#FE8463'
              }
            }
          }
        ]
      }
    }
  },
  methods: {
    initCharts(str, option) {
      this.chart = echarts.init(document.getElementById(str))
      this.chart.setOption(option)
    }
  },
  mounted() {
    this.initCharts('test1', this.option1)
    this.initCharts('test2', this.option2)
    this.initCharts('test3', this.option3)
    this.initCharts('test4', this.option4)
    const myChart = echarts.init(document.getElementById('test5'))
    // this.option5.series[0].data = this.option5.series[0].data.map((item, i) => {
    //   return {
    //     value: item.value,
    //     itemStyle: {
    //       color: i === this.option5.series[0].data.length - 1 ? '#FE8463' : '#9BCA63'
    //     }
    //   }
    // })
    // console.log(this.option5)
    myChart.setOption(this.option5)
    myChart.on('click', param => {
      console.log(param)
      const t = param.seriesIndex
      console.log(t)
      const arr = ['#9BCA63', '#911111']
      this.option5.series.forEach((item, i) => {
        this.option5.series[i].data = this.option5.series[i].data.map((item, j) => {
          return {
            value: item.value,
            itemStyle: {
              color: param.dataIndex === j && t === i ? '#FE8463' : arr[i]
            }
          }
        })
      })
      myChart.setOption(this.option5)
    })
  }
}
</script>
<style rel="stylesheet/scss" lang="scss" scoped>
.chartsTest {
  padding: 12px;
  #test1,
  #test2,
  #test3,
  #test4,
  #test5 {
    height: 300px;
  }
  .mt10 {
    margin-top: 10px;
  }
  .header {
    h3 {
      margin: 0;
      padding: 0;
    }
    font-size: 12px;
    height: 20px;
    line-height: 20px;
    color: #ccc;
  }
}
</style>

