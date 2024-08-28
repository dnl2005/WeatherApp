<script setup>
import { ref } from 'vue';
import Clock from './Clock.vue';
import Greetings from './Greetings.vue';

const props = defineProps({
  city: String
})
</script>

<template>
  <header>
    <span class="city">{{ city }}</span>
    <Greetings />
    <Clock @time="$emit('bg', $event)" />
  </header>
</template>

<style scoped>
.city {
  position: absolute;
  left: 140px;
}

header {
  position: relative;
  padding: 40px 0 0;
  font-size: 2rem;
}
</style>