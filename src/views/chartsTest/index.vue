<template>
  <div class="chartsTest">
    <el-row :gutter="12">
      <el-col :span="12">
        <el-card shadow="never">
          <div id="test1"></div>
          <div id="test2"></div>
        </el-card>
      </el-col>
      <el-col :span="12">
        <el-card shadow="never">
          <div id="test3"></div>
          <div id="test4"></div>
        </el-card>
      </el-col>
    </el-row>
    <el-card class="mt10"
             shadow="never">
      <div class="header">
        <h3>垂直居中</h3>
      </div>
    </el-card>
  </div>
</template>
<script>
import echarts from 'echarts'
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
        backgroundColor: '#2c343c',
        visualMap: {
          show: false,
          min: 80,
          max: 600,
          inRange: {
            colorLightness: [0, 1]
          }
        },
        series: [
          {
            name: '访问来源',
            type: 'pie',
            radius: '55%',
            data: [
              { value: 235, name: '视频广告' },
              { value: 274, name: '联盟广告' },
              { value: 310, name: '邮件营销' },
              { value: 335, name: '直接访问' },
              { value: 400, name: '搜索引擎' }
            ],
            roseType: 'angle',
            label: {
              normal: {
                textStyle: {
                  color: 'rgba(255, 255, 255, 0.3)'
                }
              }
            },
            labelLine: {
              normal: {
                lineStyle: {
                  color: 'rgba(255, 255, 255, 0.3)'
                }
              }
            },
            itemStyle: {
              normal: {
                color: '#c23531',
                shadowBlur: 200,
                shadowColor: 'rgba(0, 0, 0, 0.5)'
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
  }
}
</script>
<style rel="stylesheet/scss" lang="scss" scoped>
.chartsTest {
  padding: 12px;
  #test1,
  #test2,
  #test3,
  #test4 {
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

