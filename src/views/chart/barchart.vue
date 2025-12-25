<!-- src/views/chart/barchart.vue -->
<script setup>
import * as echarts from 'echarts'
import { ref, onMounted, onBeforeUnmount } from 'vue'

const chart = ref()
let myChart = null

onMounted(() => {
    initChart()
})

onBeforeUnmount(() => {
  if (myChart) {
    myChart.dispose()
  }
})

function initChart() {
    if (chart.value) {
      myChart = echarts.init(chart.value)
      
      // 定义图表配置
      const option = {
          title: {
              text: 'ECharts 入门示例',
              textStyle: {
                  color: '#fff',
                  fontSize: 15,
              }
          },
          tooltip: {},
          toolbox: {
              show: true,
              feature: {
                  magicType: {
                      type: ['line', 'bar']
                  },
                  restore: {},
                  saveAsImage: {},
                  dataView: {}
              }
          },
          xAxis: {
              type: 'value'
          },
          yAxis: {
              type: 'category',
              data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
          },
          series: [
              {
                  name: '销量',
                  type: 'bar',
                  data: [5, 20, 36, 10, 10, 20],
                  barWidth: 30,
                  itemStyle: {  
                      color: function(params) {
                          var colorList = [
                              '#c23531','#2f4554', '#61a0a8', '#d48265', 
                              '#91c7ae','#749f83',  '#ca8622', '#bda29a',
                              '#6e7074', '#546570', '#c4ccd3'
                          ];
                          return colorList[params.dataIndex];
                      }
                  }
              }
          ]
      };
      
      myChart.setOption(option)
      
      // 添加窗口大小调整处理
      window.addEventListener('resize', () => {
        if (myChart) {
          myChart.resize()
        }
      })
    }
}
</script>

<template>
  <div ref="chart" style="width: 100%; height: 500px;"></div>
</template>