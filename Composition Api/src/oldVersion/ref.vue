<template>
  <div class="container">
    <div class="card">
      <h1>Vue Composition Api</h1>
      <hr>
      <p>Название: <strong>{{ name }}</strong></p>
      <p>Версия: <strong>{{ version }}</strong></p>

      <button class="btn" @click="change">Изменить</button>
    </div>
  </div>
</template>

<script>
//испортируем функцию из композитион из вью 
import {ref} from 'vue'
export default {
  setup(){
    const name = ref('VueJs')
    const version = ref(3)

    function changeInfo(){
     name.value = 'Vue Js!'
     version.value = 4
    }
    //in setup we always retirn a object
    return{
      name, 
      version,
      change: changeInfo

    }
  }
}
</script>