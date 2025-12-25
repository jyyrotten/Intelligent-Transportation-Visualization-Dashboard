<!-- src/views/chart/map.vue -->
<script setup>
import guangxiMap from '../../assets/json/guangxiamap.json'
import { ref, onMounted, onBeforeUnmount, effect } from 'vue'
import * as echarts from 'echarts'

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
    echarts.registerMap('广西', guangxiMap)
    
    const option = {
      // 完整的geo配置
      geo: {
        map: '广西',
        label: {
          show: true,
          color: '#333333',
          fontSize: 10
        },
        itemStyle: {
          areaColor: '#4D98F9',
          borderColor: '#3fffff',
          color: '#ffffff'
        },
        emphasis: {
          label: {
            show: true,
            color: '#333333',
            fontSize: 14
          },
          itemStyle: {
            color: '#FFD700',
            borderColor: '#FF0000',
            
          }
        }
      },
      series: [
        // 地图系列
        {
          type: 'map',
          map: '广西',
          label: {
            show: false
          },
          itemStyle: {
            areaColor: '#4D98F9',
            borderColor: '#3fffff',
            color: '#ffffff'
          },
          emphasis: {
            label: {
              show: true,
              color: '#333333',
              fontSize: 14
            },
            itemStyle: {
              color: '#FFD700',
              borderColor: '#FF0000',
              borderWidth: 2
            }
          }
        },
        // 散点图系列（独立的series）
        {
          type: 'effectScatter',
          coordinateSystem: 'geo',
          symbolSize: 10,
          rippleEffect: {
            brushType: 'stroke'
          },
          label: {
            formatter: '{b}',
            position: 'right',
            show: true
          },
          itemStyle: {
            shadowBlur: 10,
            shadowColor: '#333333'
          },
          // 完整的广西地级市数据
          data: [
            {name:'南宁市',value:[108.320007,22.82402]},
            {name:'柳州市',value:[109.411736,24.314617]},
            {name:'桂林市',value:[110.299121,25.274215]},
            {name:'梧州市',value:[111.297563,23.474863]},
            {name:'北海市',value:[109.119254,21.473343]},
            {name:'防城港市',value:[108.345477,21.614409]},
            {name:'钦州市',value:[108.624175,21.967127]},
            {name:'贵港市',value:[109.598808,23.093599]},
            {name:'玉林市',value:[110.154393,22.63136]},
            {name:'百色市',value:[106.616285,23.897742]},
            {name:'贺州市',value:[111.552056,24.414141]},
            {name:'河池市',value:[108.062105,24.695899]},
            {name:'来宾市',value:[109.229772,23.733766]},
            {name:'崇左市',value:[107.353926,22.404108]}
          ]
        },
        {
          type:'lines',
          effect: { 
            show: true,
            period:2,
            shmbol:'arrow',
            symbolSize:8
          },
          lineStyle:{
            color:'rgb(255, 200, 100)',
            width:1,
            opacity:1,
            curveness:0.3,
          },
          data:[
            [
              {coord:[110.154393,22.63136],},
              {coord:[108.320007,22.82402]},
            ],
            // 柳州市 → 南宁市
    [
      {coord:[109.411736,24.314617]},
      {coord:[108.320007,22.82402]}
    ],
    // 桂林市 → 南宁市
    [
      {coord:[110.299121,25.274215]},
      {coord:[108.320007,22.82402]}
    ],
    // 梧州市 → 南宁市
    [
      {coord:[111.297563,23.474863]},
      {coord:[108.320007,22.82402]}
    ],
    // 北海市 → 南宁市
    [
      {coord:[109.119254,21.473343]},
      {coord:[108.320007,22.82402]}
    ],
    // 防城港市 → 南宁市
    [
      {coord:[108.345477,21.614409]},
      {coord:[108.320007,22.82402]}
    ],
    // 钦州市 → 南宁市
    [
      {coord:[108.624175,21.967127]},
      {coord:[108.320007,22.82402]}
    ],
    // 贵港市 → 南宁市
    [
      {coord:[109.598808,23.093599]},
      {coord:[108.320007,22.82402]}
    ],
    // 百色市 → 南宁市
    [
      {coord:[106.616285,23.897742]},
      {coord:[108.320007,22.82402]}
    ],
    // 贺州市 → 南宁市
    [
      {coord:[111.552056,24.414141]},
      {coord:[108.320007,22.82402]}
    ],
    // 河池市 → 南宁市
    [
      {coord:[108.062105,24.695899]},
      {coord:[108.320007,22.82402]}
    ],
    // 来宾市 → 南宁市
    [
      {coord:[109.229772,23.733766]},
      {coord:[108.320007,22.82402]}
    ],
    // 崇左市 → 南宁市
    [
      {coord:[107.353926,22.404108]},
      {coord:[108.320007,22.82402]}
    ]

          ]
        }
      ]
    }
    
    myChart.setOption(option)
    
    const handleResize = () => {
      if (myChart) {
        myChart.resize()
      }
    }
    
    window.addEventListener('resize', handleResize)
    
    onBeforeUnmount(() => {
      window.removeEventListener('resize', handleResize)
    })
  }
}
</script>

<template>
 <div ref="chart" class="guangximap" ></div>
</template>