<script setup>
import Waterpond from './chart/waterpond.vue';
import Rosechart from './chart/rosechart.vue';
import Map from './chart/map.vue';
</script>

<template>
 <div class="modulethird">
    <div class="modulethird-left">
      <Map/>
    </div>
    <div class="modulethird-right">
      <div class="waterpond-container">
        <Waterpond/>
      </div>
      <div class="rosechart-container">
        <Rosechart/>
      </div>
      
    </div>
  </div>
</template>

<style>

</style>