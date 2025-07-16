<script setup>
    import PCcomponent from './PCcomponent.vue'
    import ServerComponent from './ServerComponent.vue'

</script>


<template>
    <div class="pc-container">
        <h1 class="green"> PCs </h1>
            <PCcomponent/>
            <PCcomponent/>
            <PCcomponent/>
            <PCcomponent/>
            <PCcomponent/>
    </div>
    <div class="server-container">
        <h1 class="green"> Server </h1>
            <ServerComponent/>
            <ServerComponent/>
    </div>
</template>



<style scoped>
.pc-container {
  display: flex;
  flex-direction: column;
  gap: 10px;
  padding: 20px;
}

.server-container {
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
</style>