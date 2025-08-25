<script setup>
import axios from 'axios'
import { ref } from 'vue'

const apiUrl = import.meta.env.VITE_API_URL

const allScodes = ref()

axios.post(apiUrl + '/scode/all',
        )
        .catch(error => {
                console.log(error)
        })
        .then(response => {
            allScodes.value = response.data  
})

</script>

<template>

<div class="modal fade" tabindex="-1" id="ModalScodesAll">
    
  <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header sticky-top bg-white">
          <h5 class="modal-title"><i class="bi bi-book me-2"></i>Перегляд всіх скодів</h5> 
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
  
  <div class="mt-2 px-1">
      
<div class="container col-auto pt-2">

<div class="rounded border mb-3" v-for="(scode, index) in allScodes">
  <div class="p-2 fw-bolder">Scode {{ scode.scode }}</div>
  <div class="p-2">{{ scode.error }}</div>
  <div class="p-2">{{ scode.solution }}</div>
</div>

</div>
  

  

  
  </div>
      
      </div>
    </div>
  </div>

</template>

