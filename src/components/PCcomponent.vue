<template>
  <div class="PCcomponent">
    <img 
      class="PCicon" 
      src="../assets/PCScreen_unlocked.svg" 
      alt="PCicon" 
      @click="handleScreenClick"
    />
    <img
        v-if="showOverlay"
        class="PostIt"
        src="../assets/PostIt.svg"
        alt="Overlay"
        @click="handlePostItClick"
      />
  </div>
</template>

<script setup>
import { ref } from 'vue'

const screenUnlocked = ref("../assets/PCScreen_unlocked.svg")
const screenLocked = ref("../assets/PCScreen_locked.svg")
const screenState = screenUnlocked

const showOverlay = ref(true)

function handlePostItClick() {
  showOverlay.value = false
}

function handleScreenClick() {
  src = "../assets/PCScreen_locked.svg"
}


</script>

<style scoped>
.PCcomponent {
  padding: 10px;
}


.PCicon {
  width: 150px;
  height: auto;
  cursor: pointer;
}

.PostIt {
  position: relative;
  top: -70px;
  left: -55px;
  width: 50px;
  height: 50px;
  cursor: pointer;
}
</style>