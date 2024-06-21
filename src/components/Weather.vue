<script setup>

import { ref, onMounted } from 'vue'

const cities = ref([])
const weatherInfo = ref(null)
const selectedCity = ref(null)

async function getCities() {
  const response = await fetch('https://www.el-tiempo.net/api/json/v2/provincias/33/municipios')
  const responseBody = await response.json()
  cities.value = responseBody.municipios.map(c => ({
    city: c.NOMBRE,
    id: c.CODIGOINE.substring(0, 5)
  }))
}

async function getWeatherInformation(id) {
  const response = await fetch(`https://www.el-tiempo.net/api/json/v2/provincias/33/municipios/${id}`)
  const responseBody = await response.json()
  weatherInfo.value = {
    city: responseBody.municipio.NOMBRE,
    stateSky: responseBody.stateSky.description, 
    temperature: responseBody.temperatura_actual
  }
}

function updateWeather(e) {
  getWeatherInformation(e.target.value)
}
onMounted(() => {
  getCities()
  getWeatherInformation('33044') 
})



</script>

<template>

<div>
    <select @change="updateWeather" v-model="selectedCity">
      <option v-for="city in cities" :key="city.id" :value="city.id">
        {{ city.city }}
      </option>
    </select>
    <div v-if="weatherInfo">
      <h2>El tiempo en {{ weatherInfo.city }}</h2>
      <p>Tº {{ weatherInfo.temperature }}°C</p>
      <p> {{ weatherInfo.stateSky }}</p>
    
    </div>
  </div>

</template>



<style scoped lang="scss">


</style>