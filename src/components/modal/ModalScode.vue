<script setup>
import stacker from '../../assets/stacker_02.jpg'
import circles from '../../assets/Fidget-spinner.gif'
import dribbble from '../../assets/dribbble_15.gif'
const props = defineProps({
  apiSearch: Object,
  loading: Boolean,
  error: Boolean,
  success: Boolean
})

</script>

<template>
<div class="modal fade" tabindex="-1" id="ModalScode">
  <div class="modal-dialog 1modal-dialog-centered">
    <div class="modal-content">
  
  <!-- loading -->
    <div class="loading" v-if="loading">
      <div class="modal-header border-bottom-0">  
        <h5 class="modal-title text-center col-11">Шукаю інформацію ...</h5>
          <button type="button"
              class="btn-close col-1"
              data-bs-dismiss="modal"
              aria-label="Close">
          </button>
      </div>
      <div class="text-center pb-3"><img :src="circles" alt="stacker" class="mb-2 1me-4 text-center 1sticky-top"></div>
    </div>

  <!-- error -->
  <div class="error" v-if="error">
    <div class="modal-header border-bottom-0 error">  
        <h5 class="modal-title text-center col-11">Вказаний скод не знайдений!</h5>
          <button type="button"
              class="btn-close col-1"
              data-bs-dismiss="modal"
              aria-label="Close"
              @click="toggle()">
          </button>
      </div>
      <div class="text-center"><img :src="dribbble" alt="stacker" class="" width="80%"></div>
      <div class="form-text text-center fst-italic fs-6 container mt-4">Переглянути список всіх скодів можна в меню -> всі скоди</div> 
      <div class="my-4 text-center container 1bb">
                <button type="button"
                            class=" btn btn-outline-dark col-12 fs-5 rounded-5 py-2"
                            data-bs-toggle="modal"
                            data-bs-target="#ModalFeedback">
                            <i class="bi bi-rocket-takeoff pe-1"></i>
                            Додати своє рішення
                    </button>
      </div>
  </div>
  
  <!-- success -->
   <div class="success" v-if="success">
          <div class="modal-header">
            <h5 class="modal-title">Код помилки: {{ apiSearch.scode }}</h5>
            <button type="button" class="btn-close me-1" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="mt-2 1bb"> 
            <div class="px-1">
              <p class="text-center t18 fw-bold my-3 px-3">{{ apiSearch.error }}</p>
              <p class="t18 1px-4 mx-2 px-3" style="text-align: justify;">{{ apiSearch.solution }}</p>
            <div v-if="apiSearch.comment !== null">
              <p class="text-center t18 mx-2 px-3 fw-bold my-3 fst-italic"> <i class="bi bi-pen pe-2"></i>Коментарі інженерів</p>
              <p class="t18 mx-2 px-3 1my-0 1fst-italic" style="text-align: justify;">{{ apiSearch.comment }}</p>
            </div>
            <div class="mx-2 my-4 1mt-3 1mb-2 1bb text-center container">
              <button type="button"
                          class="btn btn-outline-dark col-12 fs-5 rounded-5 py-2"
                          data-bs-toggle="modal"
                          data-bs-target="#ModalFeedback">
                          <i class="bi bi-rocket-takeoff pe-1"></i>
                          Додати своє рішення
                  </button>
            </div><img :src="stacker" alt="stacker" class="mb-4 me-4 text-center" width="100%"></div>
      </div>
    </div>
    
    </div>
  </div>
</div>
</template>
