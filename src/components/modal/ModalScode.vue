<script setup>
import { ref } from 'vue';
import stacker from '../../assets/stacker_02.jpg'

const props = defineProps({
  resultApiScode: Object
})

</script>

<template>

<div class="modal fade" tabindex="-1" id="ModalScode">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" v-if="resultApiScode.scode !== null">Код помилки: {{ resultApiScode.scode }}</h5> 
        <button type="button" class="btn-close me-1" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="mt-2"> 
        <div class="px-1">
          <p class="text-center t18 fw-bold my-4 px-3">{{ resultApiScode.error }}</p>
          <p class="t18 1px-4 mx-2 px-3" style="text-align: justify;">{{ resultApiScode.solution }}</p>
          
          <div v-if="resultApiScode.comment !== null">
            <p class="1text-center 1t18 mx-2 px-3 1fw-bold my-0 fst-italic"> <i class="bi bi-pen pe-2"></i>Найкращі практики</p>
            <div class="px-4"><hr class="mt-0 mb-1 px-3"></div>
            <p class="t18 mx-2 px-3 my-0 1fst-italic" style="text-align: justify;">{{ resultApiScode.comment }}</p>
          </div>

          <div class="mx-2 my-4 1mt-3 1mb-2 1bb text-center">
            <button type="button"
                        class=" btn btn-outline-dark col-10 fs-5 rounded-5 py-2"
                        data-bs-toggle="modal"
                        data-bs-target="#ModalFeedback">
                        <i class="bi bi-rocket-takeoff pe-1"></i>
                        Додати своє рішення
                </button>
          </div>


          <img :src="stacker" alt="stacker" class="mb-4 me-4 text-center" v-if="resultApiScode.scode !== null" width="100%">
        </div>
    </div>
    </div>
  </div>
</div>

</template>
