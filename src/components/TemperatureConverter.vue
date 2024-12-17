<template>
  <div class="temperature-converter">
    <h1>Conversor de Temperatura</h1>
    
    <div class="converter-content">
      <div class="temperature-row">
        <label>Ingrese Temperatura °C</label>
        <input 
          type="text" 
          v-model="celsius"
          placeholder="0"
        >
      </div>

      <div class="temperature-row">
        <label>Conv. Temperatura °F:</label>
        <span :style="{ color: textColor }">{{ fahrenheit }}</span>
      </div>

      <div class="temperature-row">
        <label>Conv. Temperatura °K:</label>
        <span :style="{ color: textColor }">{{ kelvin }}</span>
      </div>
    </div>

    <p class="answers">Respuestas: 1:c - 2:b - 3:c - 4:a</p>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const celsius = ref('')

const fahrenheit = computed(() => {
  if (celsius.value === '') return ''
  return ((Number(celsius.value) * 9/5) + 32).toFixed(2)
})

const kelvin = computed(() => {
  if (celsius.value === '') return ''
  return (Number(celsius.value) + 273.15).toFixed(2)
})

const textColor = computed(() => {
  const temp = Number(celsius.value)
  if (celsius.value === '') return 'black'
  if (temp <= 0) return 'blue'
  if (temp > 0 && temp < 15) return 'magenta'
  return 'red'
})
</script>

<style scoped>
.temperature-converter {
  max-width: 800px;
  margin: 20px auto;
  font-family: Arial, sans-serif;
}

h1 {
  font-size: 2.5em;
  margin-bottom: 30px;
  border-bottom: 1px solid #ccc;
  padding-bottom: 10px;
  font-weight: bold;
}

.converter-content {
  margin-left: 20px;
}

.temperature-row {
  margin: 15px 0;
  display: flex;
  align-items: center;
}

label {
  min-width: 200px;
  font-size: 1em;
}

input {
  width: 150px;
  padding: 3px;
  margin-left: 5px;
  font-size: 1em;
}

span {
  margin-left: 5px;
  font-size: 1em;
}

.answers {
  margin-top: 50px;
  padding: 20px;
  border-top: 1px solid #ccc;
  font-weight: bold;
}
</style>