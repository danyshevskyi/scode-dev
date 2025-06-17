<script setup>
import { ref } from 'vue';
import stacker from '../../assets/stacker3.jpg'

const props = defineProps({
  resultApiScode: Object
})

</script>

<template>

<div class="modal fade" tabindex="-1" id="ModalScode">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title">Код помилки: {{ resultApiScode.data.scode }}</h5> 
        <button type="button" class="btn-close me-1" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
  
        <div class="mt-2">
      
               
              <div class="px-1">
                <!-- <p class="text-center t18 fw-bold mt-2">Код помилки: {{ resultApiScode.data.scode }}</p> -->
                <p class="text-center t18 fw-bold my-4 px-3">{{ resultApiScode.data.error }}</p>
                
                <!-- <p class="text-center t18 px-4 mt-4 fw-bold">Опис помилки</p> -->
                <p class="1text-center t18 1px-4 mx-2 px-3" style="text-align: justify;">{{ resultApiScode.data.solution }}</p>
                <img :src="stacker" alt="stacker" class="mb-4 me-4 text-center">
               
                

              </div>

                  
                

                  
                

                
                

      </div>
    </div>
  </div>
</div>

</template>

<style scoped>
</style>