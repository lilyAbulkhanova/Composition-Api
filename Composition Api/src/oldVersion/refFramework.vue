<template>
    <div class="container">
      <div class="card">
        <h1>Vue Composition Api</h1>
        <hr>
        <p>Название: <strong>{{ framework.name }}</strong></p>
        <p>Версия: <strong>{{ framework.version }}</strong></p>
  
        <button class="btn" @click="changeInfo">Изменить</button>
      </div>
    </div>
  </template>
  
  <script>
  //испортируем функцию из композитион из вью 
  import {ref} from 'vue'
  export default {
    setup(){
      const framework = ref({
        name: 'Vue js',
        version: 3
      })
  
      function changeInfo(){
       framework.value.name = 'VueJs!'
       framework.value.version = 4
      }
      //in setup we always return a object
      return{
        name: framework.value.name,
        version: framework.value.version,
        framework: framework,
        changeInfo
      }
    }
  }
  </script>