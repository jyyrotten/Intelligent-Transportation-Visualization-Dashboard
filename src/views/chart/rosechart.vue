<!-- src/views/chart/rosechart.vue -->
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
    
    const option = {
      tooltip: {},
      series: [
        {
          type: "pie",
          roseType: 'area',
          radius: [20, 80],
          data: [
            { value: 50, name: 'A' },
            { value: 38, name: 'B' },
            { value: 32, name: 'C' },
            { value: 30, name: 'D' },
            { value: 20, name: 'E' },
          ],
          label: {
            show: true,
            formatter: '{b}：{c} ({d}%)',
            textStyle: {
              color: '#fff'
            }
          }
        }
      ]
    }
    
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
  <div style="transform: translateY(-30px);">
    <div ref="chart" style="width: 600px;height: 400px;"></div>
  </div>
</template>