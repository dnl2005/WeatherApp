<script setup>
import { ref, computed } from 'vue';

let hours = ref('')
let minuts = ref('')
let seconds = ref('')

let time = ref(`--:--:--`)

const clock = computed(setInterval(()=>{
  let curTime = new Date()
  if (curTime.getHours() < 10) {
    hours.value = `0${curTime.getHours()}`
  } else {
    hours.value = `${curTime.getHours()}`
  }

  if (curTime.getMinutes() < 10) {
    minuts.value = `0${curTime.getMinutes()}`
  } else {
    minuts.value = `${curTime.getMinutes()}`
  }

  if (curTime.getSeconds() < 10) {
    seconds.value = `0${curTime.getSeconds()}`
  } else {
    seconds.value = `${curTime.getSeconds()}`
  }

  time.value = `${hours.value}:${minuts.value}:${seconds.value}`
},500))

const emit = defineEmits()
emit("time", new Date().getHours())
</script>

<template>
  <span class="clock">{{ time }}</span>
</template>

<style scoped>
.clock{
  position: absolute;
  right: 140px;
}
</style>