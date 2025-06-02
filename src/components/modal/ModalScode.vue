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
        <h5 class="modal-title">SCODE {{ resultApiScode.data.scode }}</h5> 
        <button type="button" class="btn-close me-1" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
  
        <div class="mt-2 mx-auto">
      
               
              <div>
                <p class="text-center t18 fw-bold mt-2">Опис проблеми</p>
                <p class="1text-center t18 px-4">{{ resultApiScode.data.text }}</p>
                
                <slot name="test"></slot>
                

              </div>

                  
                <img :src="stacker" alt="stacker"/>

                  
                
                <a class="text-decoration-none text-black" href="https://www.linkedin.com/in/danyshevskyi/" target="_blank"> 
                    <div class="text-center mt-3 mb-4" style="font-size: 13px;">Oleksii Danyshevskyi &copy; 2025    
                    <i class="bi bi-linkedin"></i>
                  </div>
                </a>
                
                

      </div>
    </div>
  </div>
</div>

</template>

<style scoped>
</style>