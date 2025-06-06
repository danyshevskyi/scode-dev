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
        <h5 class="modal-title">Опис рішення</h5> 
        <button type="button" class="btn-close me-1" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
  
        <div class="mt-2 1mx-auto 1bb">
      
               
              <div class="container 1px-3">
                <p class="text-center t18 fw-bold mt-2">Код помилки: {{ resultApiScode.data.scode }}</p>
                <p class="text-center t18 fw-bold mt-2">{{ resultApiScode.data.error }}</p>
                
                <!-- <p class="text-center t18 px-4 mt-4 fw-bold">Опис помилки</p> -->
                <p class="1text-center t18 1px-4 mx-4" style="text-align: justify;">{{ resultApiScode.data.solution }}</p>
                <img :src="stacker" alt="stacker" class="mb-3 mx-auto 1bb">
                <slot name="test"></slot>
                

              </div>

                  
                

                  
                

                
                

      </div>
    </div>
  </div>
</div>

</template>

<style scoped>
</style>