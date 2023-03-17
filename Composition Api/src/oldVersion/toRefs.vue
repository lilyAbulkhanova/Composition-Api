<template>
    <div class="container">
      <div class="card">
        <h1>Vue Composition Api</h1>
        <hr>
        <p>Название: <strong>{{ name }}</strong></p>
        <p>Версия: <strong>{{ version }}</strong></p>
  
        <button class="btn" @click="changeInfo">Изменить</button>
      </div>
    </div>
  </template>
  
  <script>
  //испортируем функцию из композитион из вью 
  import {ref, reactive, toRefs} from 'vue'
  export default {
    setup(){
      //toRefs help us convert reactive as ref 
      const framework = reactive({
        name: 'Vue js',
        version: 3
      })
  
      function changeInfo(){
       framework.name = 'VueJs',
       framework.version = 4
      }
      //in setup we always return a object
      return{
        ...toRefs(framework),
        framework: framework,
        changeInfo
      }
    }
  }
  </script>