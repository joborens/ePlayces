<template>
    <div class="upgrade-container">
    <h1 class="green"> Upgrades </h1>
    <button v-for="(button, index) in buttons" :key="index" @click="handleClick(index)">
       {{ button.count }}/{{ button.max }} - {{ button.effect }} - 
       <img class="coin" src="../assets/Coin.svg" alt="coin"/> {{ button.cost }}
       <div class="progress">
          <div class="progress-bar" :style="{ width: calculateFill(button.count, button.max) + '%' }"></div>
        </div>
    </button>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const buttons = ref([
  { count: 1, max: 5, effect: 'Add new PC', baseCost: 1, cost: 1, decay: 0},
  { count: 0, max: 5, effect: 'Add new Server', baseCost: 1, cost: 1, decay: 0},
  { count: 0, max: 20, effect: 'Increase minimum password length', baseCost: 1, cost: 1, decay: 0},
  { count: 0, max: 20, effect: 'Increase minimum password length', baseCost: 1, cost: 1, decay: 0},
  { count: 0, max: 1, effect: 'Require numbers in password',  baseCost: 100, cost:  100, decay: 0},
  { count: 0, max: 1, effect: 'Require symbols in password', baseCost: 200, cost:  200, decay: 0},
  { count: 0, max: 1, effect: 'Require Two Factor Authentication', baseCost: 500, cost:  500, decay: 0},
  { count: 0, max: 1, effect: 'Encrypt data', baseCost: 1000, cost: 1000, decay: 0},
  { count: 0, max: 1, effect: 'Train Employees', baseCost: 100, cost: 100, decay: 0.1}
])

function handleClick(index) {
    if (buttons.value[index].count < buttons.value[index].max)
    {
        buttons.value[index].count = Math.min(buttons.value[index].count + 1 , buttons.value[index].max)
    }
    updateCost(index)
}

function updateCost(index) {
  buttons.value[index].cost = buttons.value[index].count * buttons.value[index].baseCost
}

function calculateFill(count, max) {
  return Math.min((count / max) * 100, 100)
}

let intervalId = null
onMounted(() => {
  intervalId = setInterval(() => {
    buttons.value.forEach(button => {
      if (button.count > 0 && button.decay != 0) {
        button.count = Math.max(button.count - button.decay, 0).toFixed(1)
      }
    })
  }, 1000)
})

onUnmounted(() => {
  clearInterval(intervalId)
})


</script>

<style scoped>
.upgrade-container {
  display: flex;
  flex-direction: column;
  gap: 10px;
  padding: 20px;
}

button {
  padding: 10px 20px;
  background-color: #007BFF;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.coin {
  width: 12px;
  height: 12px;
}

.progress {
  background-color: rgba(255, 255, 255, 0.3);
  border-radius: 4px;
  overflow: hidden;
  height: 6px;
  margin-top: 4px;
}

.progress-bar {
  background-color: #fff;
  height: 100%;
  transition: width 0.3s ease;
}
</style>

