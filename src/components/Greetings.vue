<script setup>
import { ref, computed } from 'vue';

let hour = ref(new Date().getHours())

const greet = computed(() => {
  if (5 <= hour.value && hour.value < 12) {
    return "Доброе утро"
  } else if (12 <= hour.value && hour.value < 18) {
    return "Добрый день"
  } else if (18 <= hour.value && hour.value < 23) {
    return "Добрый вечер"
  } else if (hour.value >= 0 || 23 <= hour.value) {
    return "Доброй ночи"
  }
})
</script>

<template>
  <span class="greet">{{ greet }}</span>
</template>

<style scoped>
.greet{
  position: absolute;
  left: 50%;
  transform: translate(-50%);
}
</style>