<template>
    <div class="container">
      <div class="card">
        <h1>Vue Composition Api</h1>
        <div class="form-control">
          <input type="text" v-model="firstName">
        </div>
        <button class="btn" @click="changeInfo">Изменить</button>
      </div>
      <Framework 
        :name="name" 
        :version="version"
        @change-version="changeVersion"
      />
    </div>
  </template>
  
  <script>
  //испортируем функцию из композитион из вью 
  import {ref, reactive, toRefs, computed, provide, onBeforeMount,onBeforeUpdate} from 'vue'
  import Framework from './components/Framework.vue'
  
  export default { 
    setup(){
      const name = ref('VueJs')
      const version = ref(3)
  
      const firstName = ref('')
      //toRefs help us convert reactive as ref 
      const framework = reactive({
        name: 'Vue js',
        version: 3
      })
      function changeVersion(num){
        version.value = num
      }
  
      provide('name', name)
      provide('version', version)
      /* const doubleVersion = computed( () => {
        return version.value * 2
      }) */
  
      function changeInfo(){
       name.value = 'VueJs!',
       version.value = 4
      }
      //in setup we always return a object
      return{
        name,
        version,
        changeInfo,
        firstName,
        changeVersion
      }
    },
    components:{Framework}
  }
  </script>