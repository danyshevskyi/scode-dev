<script setup>
import axios from "axios";
const urlAnalytics = import.meta.env.VITE_URL_API_ANALYTICS;

async function sendAnalytics(request) {
  axios.post(urlAnalytics + "/" + request).catch((error) => {
    console.log(error);
  });
}
</script>

<template>
  <div class="modal fade" tabindex="-1" id="mod_about">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">
            <i class="bi bi-info-circle ps-1 pe-2"></i>Про додаток
          </h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>

        <div class="mt-2 px-2">
          <div class="container col-auto t18">
            <p class="mt-1 mb-0" style="text-align: justify; text-indent: 25px">
              Scode - це додаток пошуку рішень для інженерів з обслуговування
              банкоматів Wincor Nixdorf на базі контролерів CMD-V4.
            </p>

            <p class="text-center my-3">
              Доступ із будь-якого пристрою за адресою:<br />
              <a href="https://dov.pp.ua/scode" class="text-decoration-none">
                https://dov.pp.ua/scode</a
              >
            </p>
          </div>

          <div class="mx-auto 1pb-1">
            <a
              class="text-decoration-none text-black"
              href="https://github.com/danyshevskyi/scode-dev"
              target="blank"
              @click="getApi(apiFooter)"
            >
            </a>
          </div>

          <div class="d-flex justify-content-center mt-4 mb-2">
            <button
              type="button"
              id="aboutButReg"
              class="btn btn-outline-dark rounded-5 col-11 py-2 fs-5 1px-5 text-decoration-none"
              style="margin-bottom: 13px"
              data-bs-toggle="modal"
              data-bs-target="#ModalFeedback"
              @click="sendAnalytics('feedback')"
            >
              <i class="bi bi-pen ps-1 pe-2"></i>Зворотний зв'язок
            </button>
          </div>

          <div class="mx-auto pb-3">
            <a
              class="text-decoration-none text-black"
              href="https://github.com/danyshevskyi/scode-dev"
              target="blank"
              @click="getApi(apiFooter)"
            >
            <div class="text-center my-2">
                Powered by laravel 12.x + Vue.js
              </div>
              <div class="text-center my-2">
                <i class="bi bi-github pe-2"></i>Scode on GitHub
              </div>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
