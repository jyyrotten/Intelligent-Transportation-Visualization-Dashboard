<script setup>
 import { ref } from 'vue'

const modulefirstList = ref([
  { title: '桥梁', num: 3434, unit: '个' },
  { title: '桥梁', num: 3434, unit: '个' },
  { title: '桥梁', num: 3434, unit: '个' },
  { title: '桥梁', num: 3434, unit: '个' },
  { title: '桥梁', num: 3434, unit: '个' },
  { title: '桥梁', num: 3434, unit: '个' },
  { title: '桥梁', num: 3434, unit: '个' },
  { title: '桥梁', num: 3434, unit: '个' },
  { title: '桥梁', num: 3434, unit: '个' }
])
</script>

<template>
  <div class="modulefirst">
    <ul>
      <li v-for="(v, i) in modulefirstList" :key="i">
        <div class="modulefirst-title">{{ v.title }}</div>
        <div class="">
          <span class="modulefirst-num">{{ v.num }}</span>
          <span class="modulefirst-unit">{{ v.unit }}</span>
        </div>
      </li>
    </ul>
  </div>
</template>




<style>


</style>