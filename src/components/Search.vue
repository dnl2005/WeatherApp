<script setup>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { faMagnifyingGlass } from "@fortawesome/free-solid-svg-icons";
import { reactive, ref } from 'vue';
import axios from "axios";

const emit = defineEmits()

let city = ref("")

const post = () => {
  axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${city.value}&units=metric&appid=3d9de74844d28377e81415151cbe6a66`)
  .then(res => emit("search", res.data))

  city.value = ""
}
</script>

<template>
  <form class="input-wrapper" @submit.prevent>
    <input type="text" placeholder="Поиск по городу (Англ)" v-model="city">
    <button @click="post()">
      <FontAwesomeIcon :icon="faMagnifyingGlass" style="color: white; height: 25;" />
    </button>
  </form>
</template>

<style scoped>
.input-wrapper {
  margin: 150px auto 0;
  padding: 15px 60px;
  background: var(--section);
  border-radius: 12px;
  max-width: 600px;
  width: 100%;
  display: flex;
  gap: 20px;
}

input {
  background: none;
  outline: none;
  border: none;
  color: white;
  width: 100%;
  font-size: 1rem;
  -webkit-text-fill-color: white;
}

button {
  background: none;
  border: none;
  cursor: pointer;
}
</style>