<!-- src/views/chart/peichart.vue -->
<script setup>
import { ref } from 'vue'
import { Charts } from '@kjgl77/datav-vue3'

const option = ref({
  series: [
    {
      type: 'gauge',
      data: [{ name: 'itemA', value: 55 }],
      center: ['50%', '55%'],
      axisLabel: {
        formatter: '{value}%',
        style: {
          fill: '#fff'
        }
      },
      axisTick: {
        style: {
          stroke: '#fff'
        }
      },
      animationCurve: 'easeInOutBack'
    }
  ]
})
</script>

<template>
  <Charts :option="option" style="width: 100%; height: 200px;"/>
</template>