<template>
     <div class="card">
      <p>Название: <strong>{{ name }}</strong></p>
      <p>Версия: <strong>{{ version }} ({{ doubleVersion }})</strong></p>

      <button class="btn danger" @click="changeToThree">Изменить обратно на 3 версию</button>
     </div>
</template>

<script>
import {computed, inject} from 'vue'

export default{
     props:['name', 'version'],
     emits:['change-version'],

     setup(context){
     function Change(){
          context.emit('change-version',3)
     }
     //так как version это реф поэтому добавляем value
     const version = inject('version')

     return{
       name: inject('name'),
       version: version,
       changeToThree: Change,
       doubleVersion : computed(() => version.value * 2 )
          }
     }
 }

</script>