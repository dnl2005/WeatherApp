<script setup>
import { computed, onMounted, reactive, ref } from 'vue';

import Search from './components/Search.vue';
import Header from './components/Header.vue';
import Info from './components/Info.vue';

let weather = reactive({})
let city = ref("")
let time = ref(0)

onMounted(() => {
  const bg = document.querySelector(".content")
  bg.classList.remove("morning", "day", "evening", "night")
  if (5 <= time.value && time.value < 12) {
    bg.classList.add("morning")
  } else if (12 <= time.value && time.value < 18) {
    bg.classList.add("day")
  } else if (18 <= time.value && time.value < 23) {
    bg.classList.add("evening")
  } else if (time.value >= 0 || 23 <= time.value) {
    bg.classList.add("night")
  }
})

const update = computed(()=>{
  city.value = weather.name
})
// alert("Внимание!\nПоиск погоды по городам доступен только на английском")
</script>

<template>
  <div class="content">
    <Header :city="city" @bg="res => time = res" />
    <Search @search="(data) => {weather = data, update}" />
    <Info :city="city" v-if="city" :data="weather"/>
  </div>
</template>

<style scoped>
.content {
  min-height: 100vh;
  height: 100%;

  display: flex;
  flex-direction: column;
}
</style>
