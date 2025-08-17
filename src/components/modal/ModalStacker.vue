<script setup>

import axios from 'axios'
import { ref } from 'vue'

const apiUrl = import.meta.env.VITE_API_URL

const stacker = ref()

axios.post(apiUrl + '/scode/stacker',
        )
        .catch(error => {
                console.log(error)
        })
        .then(response => {
          console.log(response.data)
            stacker.value = response.data  
        })

import stacker_01 from '../../assets/stacker_01.jpg'
import stacker_02 from '../../assets/stacker_02.jpg'

</script>

<template>

<div class="modal fade" tabindex="-1" id="ModalStacker">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <!-- <h5 class="modal-title" v-if="resultApiScode.data.scode !== null">Код помилки: {{ resultApiScode.data.scode }}</h5> -->
        <h5 class="modal-title">Схема стекера</h5>  
        <button type="button" class="btn-close me-1" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="mt-2"> 
        <div class="px-1">
          <!-- <p class="text-center t18 fw-bold my-4 px-3">{{ resultApiScode.data.error }}</p>
          <p class="1text-center t18 1px-4 mx-2 px-3" style="text-align: justify;">{{ resultApiScode.data.solution }}</p>
          <img :src="stacker" alt="stacker" class="mb-4 me-4 text-center" v-if="resultApiScode.data.scode !== null"> -->
         
          <p class="text-center 1t18 1fw-bold my-3 px-3">Горизонтальний транспорт</p>
          <img :src="stacker_01" alt="stacker" class="mb-4 me-4 text-center" width="100%">

          <p class="text-center 1t18 1fw-bold my-3 px-3">Вертикальний транспорт</p>
          <img :src="stacker_02" alt="stacker" class="mb-4 me-4 text-center" width="100%">
          

          <!-- <div class="rounded border mb-3" v-for="(scode, index) in allScodes"> -->
            <div class="rounded border mb-3">
            
              <!-- <div class="p-2 fw-bolder">Scode {{ scode.scode }}</div>
            <div class="p-2">{{ scode.error }}</div> -->

            <div class="p-2 fw-bolder">Датчик SM1</div>
            <div class="p-2">Тут йде опис датчика</div>

          </div>




        </div>
    </div>
    </div>
  </div>
</div>

</template>

<style scoped>
</style>