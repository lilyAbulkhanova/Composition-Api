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
  import {ref, reactive} from 'vue'
  export default {
    setup(){
      const framework = reactive({
        name: 'Vue js',
        version: 3
      })
  
      function changeInfo(){
       //when we use reactive we work as w normal object
       framework.name = 'VueJs',
       framework.version = 4
      }
      //in setup we always return a object
      return{
        framework: framework,
        changeInfo
      }
    }
  }
  </script>