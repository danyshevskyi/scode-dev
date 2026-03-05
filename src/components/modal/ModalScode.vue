<script setup>
import axios from "axios";
import img_loading from "../../assets/img_loading.gif";
import img_error from "../../assets/img_error.gif";
import img_stacker from "../../assets/img_stacker.jpg";
const props = defineProps({
  apiScodeSearch: Object,
  loading: Boolean,
  error: Boolean,
  success: Boolean,
});

async function sendAnalytics(request) {
  axios
        .post(import.meta.env.VITE_URL_API_ANALYTICS + '/' + request)
        .catch((error) => {
                console.log(error);
        })
}
</script>

<template>
  <div class="modal fade" tabindex="-1" id="ModalScode">
    <div class="modal-dialog 1modal-dialog-centered">
      <div class="modal-content">
        <!-- loading -->
        <div class="loading" v-if="loading">
          <div class="modal-header border-bottom-0">
            <h5 class="modal-title text-center col-11">Шукаю інформацію ...</h5>
            <button
              type="button"
              class="btn-close col-1"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="text-center pb-3">
            <img
              :src="img_loading"
              alt="stacker"
              class="mb-2 1me-4 text-center 1sticky-top"
            />
          </div>
        </div>

        <!-- error -->
        <div class="error" v-if="error">
          <div class="modal-header border-bottom-0 error">
            <h5 class="modal-title text-center col-11">
              Вказаний скод не знайдений!
            </h5>
            <button
              type="button"
              class="btn-close col-1"
              data-bs-dismiss="modal"
              aria-label="Close"
              @click="toggle()"
            ></button>
          </div>
          <div class="text-center">
            <img :src="img_error" alt="img_error" class="" width="80%" />
          </div>
          <div class="form-text text-center fst-italic fs-6 container mt-4">
            Переглянути список всіх скодів можна в меню -> всі скоди
          </div>
          <div class="my-4 text-center container 1bb">
            <button
              type="button"
              class="btn btn-outline-dark col-12 fs-5 rounded-5 py-2"
              data-bs-toggle="modal"
              data-bs-target="#ModalFeedback"
              @click="sendAnalytics('feedback')"
            >
              <!-- <i class="bi bi-rocket-takeoff pe-1"></i> -->
              Додати коментар
            </button>
          </div>
        </div>

        <!-- success -->
        <div class="success" v-if="success">
          <div class="modal-header">
            <h5 class="modal-title">Код помилки: {{ apiScodeSearch.scode }}</h5>
            <button
              type="button"
              class="btn-close me-1"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="mt-2 1bb">
            <div class="px-1">
              <p class="text-center t18 fw-bold my-3 px-3">
                {{ apiScodeSearch.error }}
              </p>
              <p class="t18 1px-4 mx-2 px-3" style="text-align: justify">
                {{ apiScodeSearch.solution }}
              </p>
              <div v-if="apiScodeSearch.comment !== null">
                <p class="text-center t18 mx-2 px-3 fw-bold my-3 fst-italic">
                  <i class="bi bi-pen pe-2"></i>Коментарі інженерів
                </p>
                <p
                  class="t18 mx-2 px-3 1my-0 1fst-italic"
                  style="text-align: justify"
                >
                  {{ apiScodeSearch.comment }}
                </p>
              </div>
              <div class="mx-2 my-4 1mt-3 1mb-2 1bb text-center container">
                <button
                  type="button"
                  class="btn btn-outline-dark col-12 fs-5 rounded-5 py-2"
                  data-bs-toggle="modal"
                  data-bs-target="#ModalFeedback"
                  @click="sendAnalytics('feedback')"
                >
                  <!-- <i class="bi bi-plus-lg pe-1"></i> -->
                  Додати коментар
                </button>
              </div>
              <img
                :src="img_stacker"
                alt="img_stacker"
                class="mb-4 me-4 text-center"
                width="100%"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
