<script setup>
import { ref } from 'vue'
// 从 datav-vue3 引入 WaterLevelPond 组件
import { WaterLevelPond } from '@kjgl77/datav-vue3'
import { Decoration2 } from '@kjgl77/datav-vue3'
const config = ref({
  data: [55],
  shape: 'round',
})
</script>

<template>
    <div class="waterpond-title">计划资金积累完成情况</div>
    <div class="waterpond-detail">
        累计完成<span>20000</span>元
    </div>
    <div class="waterpond">
<WaterLevelPond :config="config" style="width:200px;height:200px;" />
</div>
<div class="Decoration">
  <Decoration2 style="width:640px; height:10px; position: relative; top: 4px; left: -15px;" />
</div>
</template>

<style>
</style>