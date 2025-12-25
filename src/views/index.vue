<script setup>
import { ref, onMounted } from 'vue' 
import { BorderBox1 } from '@kjgl77/datav-vue3'/* 局部引入组件库 ，才能使得组件边框在页面展示*/
import ModuleTitle from './ModuleTitle.vue'
import ModuleFirst from './moduleFirst.vue'
import ModuleSecond from './moduleSecond.vue'
import ModuleThird from './moduleThird.vue'
import ModuleFourth from './moduleFourth.vue'
import '../assets/css/index.css'

let screen = ref();
const getScale=(width=1920,height=1080)=>{
     let ww=window.innerWidth/width
     let wh=window.innerHeight/height
     return ww<wh?ww :wh
}
onMounted(()=>{
     screen.value.style.transform='scale(${getScale()}) translate(-50%,-50%)'
})
window.onresize=()=>{ 
screen.value.style.transform='scale(${getScale()})translate(-50%,-50%)'
}
</script>

<template>
  <!-- 移除多余的空div，将ref放在包含所有内容的容器上 -->
  <div class="container bg" ref="screen">
    <BorderBox1 :dur="5" style="width: 100%;height: 100vh;z-index: 0; position: absolute;"></BorderBox1>
    <div style="position: relative; z-index: 1;">
      <ModuleTitle/>
      <div class="main">
        <ModuleFirst/>
        <ModuleSecond/>
        <ModuleThird/>
        <ModuleFourth/>
      </div>
    </div>
  </div> 
</template>

<style scoped>

</style>

