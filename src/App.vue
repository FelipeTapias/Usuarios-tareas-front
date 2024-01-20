<template>
 <div>
    
    <button @click="getAll">Obtener todos los usuarios</button>
    <ul>
      <li v-for="item in test" :key="item.id">
        {{ item.nombre }}
      </li>
    </ul>
 </div>
 
</template>

<script setup>

  import axios from 'axios';
  import { onMounted, ref } from 'vue';

  const test = ref([]);

  onMounted(() => {
    getAll();
  })

  async function getAll()  {
    axios.get('http://localhost:4000/api/tareas/ConsultarTareasPorIdUsuario/659ddf40e1c42bd32eab3cf4')
      .catch(error => {
        console.log('Mi error', error);
      })
      .then(data => { 
        test.value = data.data
      })
  }

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
