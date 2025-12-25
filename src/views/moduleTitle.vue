<script setup>
import { Decoration8, Decoration5 } from '@kjgl77/datav-vue3'
import '../assets/css/index.css'
</script>

<template>
  <div class="header-box">
    <Decoration8 style="width:300px; height:50px;" />

    <div>
        <h2>数据化界面</h2>
        <Decoration5 style="width:300px; height:40px;" />
    </div>

    <Decoration8 :reverse="true" style="width:300px; height:50px;" />

  </div>
</template>



<style>


</style>