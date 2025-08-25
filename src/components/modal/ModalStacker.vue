<script setup>

import axios from 'axios'
import { ref } from 'vue'

const apiUrl = import.meta.env.VITE_API_URL

const result = ref()

axios.post(apiUrl + '/scode/stacker/components',
).catch(error => {
  console.log(error)
}).then(response => {
  result.value = response.data  
})

import stacker_02 from '../../assets/stacker_02.jpg'

</script>

<template>

<div class="modal fade" tabindex="-1" id="ModalStacker">
  <div class="modal-dialog">
    <div class="modal-content">
      
      <div class="sticky-top bg-white 1shadow 1mb-3">
        <div class="modal-header">
          <h5 class="modal-title">Схема стекера</h5>  
            <button type="button" class="btn-close me-1" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="container">
          <img :src="stacker_02" alt="stacker" class="mb-2 1me-4 text-center 1sticky-top" width="100%">
        </div>
      </div>

      <div class="container"> 
        <div class="rounded border mb-3" v-for="(item, index) in result">
          <div class="p-2 fw-bolder">{{ item.component }}</div>
          <div class="p-2">{{ item.name }}</div>
          <div class="p-2">{{ item.location }}</div>
        </div>
      </div>
    
    </div>
  </div>
</div>

</template>
