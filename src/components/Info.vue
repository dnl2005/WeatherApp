<script setup>
const props = defineProps({
  city: String,
  data: Object
})
</script>

<template>
  <div class="container">
    <div class="main-info wrapper">
      <div class="main-info__left">
        <span>На 30.07 вт, 17:37</span>
        <h1>{{ city }}</h1>
      </div>
      <div class="main-info__right">
        <span>{{ data.main.temp }}°</span>
        <div class="main-info__advanced">
          <p>{{ data.weather[0].main }}</p>
          <p>{{ data.main.temp_max }}°/{{ data.main.temp_min }}°</p>
          <p>ощущается как {{ data.main.feels_like }}°</p>
        </div>
      </div>
    </div>
    <div class="second-info wrapper">
      <ul>
        <li>
          <div>
            <span>Давление</span>
          </div>
          <span>{{ data.main.pressure }} Па</span>
        </li>
        <li>
          <div>
            <span>Влажность</span>
          </div>
          <span>{{ data.main.humidity }}%</span>
        </li>
        <li>
          <div>
            <span>Видимость</span>
          </div>
          <span>{{ data.visibility }} м</span>
        </li>
        <li>
          <div>
            <span>Рассвет</span>
          </div>
          <span>{{ data.sys.sunrise }}</span>
        </li>
        <li>
          <div>
            <span>Закат</span>
          </div>
          <span>{{ data.sys.sunset }}</span>
        </li>
        <li>
          <div>
            <span>Ветер</span>
          </div>
          <span>{{ data.wind.speed }} м/с {{ data.wind.deg }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  border-radius: 12px;
  background: var(--section);
  max-width: 800px;
  width: 100%;
}

.container {
  flex-grow: 1;
  border-radius: 24px 24px 0 0;
  height: 100%;
  max-width: 1600px;
  width: 100%;
  background: var(--section);
  margin: 50px auto 0;
  padding: 50px 0;
  display: flex;
  align-items: center;
  flex-direction: column;
}

.main-info {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 100px;
}

.main-info__right {
  display: flex;
  align-items: center;
  gap: 10px;
}

.main-info__right span {
  font-weight: bold;
  font-size: 3.5rem;
  line-height: 3rem;
}

.main-info__right p {
  line-height: 0.875rem;
}

.main-info__advanced {
  text-align: end;
  font-size: 0.875rem;
}

.main-info__left h1 {
  font-size: 3rem;
  line-height: 2.5rem;
}

.second-info {
  margin-top: 20px;
  padding: 20px 100px;
  font-size: 2rem;
}

.second-info ul {
  display: flex;
  flex-direction: column;
}

.second-info li {
  display: flex;
  justify-content: space-between;
  border-bottom: 2px solid #ffffff;
  padding: 5px 30px;
}
</style>