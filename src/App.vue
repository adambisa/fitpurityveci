<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Questions from './components/Questions.vue';
import Header from './components/Header.vue';
</script>

<template>  
    <div class="center">
      <Header></Header>
      <Questions></Questions>
    </div>
</template>

<style>
  .center {
  border: 5px solid #00aae2;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

}
body{
  background-color: #ffffff;
}
</style>
