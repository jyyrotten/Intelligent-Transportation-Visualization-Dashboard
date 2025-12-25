<script setup>
import Peichart from './chart/peichart.vue';
import { Decoration4 } from '@kjgl77/datav-vue3'//引入组件要用大写
import '../assets/css/index.css' // 添加这行引入
</script>

<template>
  <div class="moduleFourthbg"style="position: relative; overflow: visible;">
    <div class="modulefourth" style="position: relative;">
      <!-- 仪表盘内容 -->
      <div class="modulefourth-list">
        <ul>
          <li v-for="(_, index) in 3" :key="index">
            <div class="peichart">
              <h4>测试路段</h4>
              <div style="width: 300px; height: 300px;">
                <Peichart />
              </div>
            </div>
          </li>
        </ul>
      </div>
     <div small-bg class="decoration">
  
</div>
      <!-- 位于仪表盘下方的模块 -->
      <div class="perchertbg" >

      </div>
    </div>
  </div>
</template>



<style>


</style>