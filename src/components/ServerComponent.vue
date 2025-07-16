<template>
  <div class="ServerComponent">
    <img class="Servericon" src="../assets/server_green.svg" alt="Servericon"/>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const ServerGreen = ref("../assets/server_green.svg")
const ServerOrange = ref("../assets/server_orange.svg")
const ServerRed = ref("../assets/server_red.svg")
const serverState = ServerGreen

</script>

<style scoped>
.ServerComponent {
  padding: 10px;
}


.Servericon {
  width: 150px;
  height: auto;
}


</style>