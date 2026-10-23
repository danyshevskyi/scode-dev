<script setup>
import axios from "axios";

// Send action
async function sendAction(action_name, action_data, is_action_save) {
  axios
    .post("https://dov.pp.ua/api/analytics/save", {
      action_name: action_name,
      action_data: action_data,
      is_action_save: is_action_save,
      project: "scode",
    })
    .catch((error) => {
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
              Доступ із будь-якого пристрою:<br />
              <a href="https://scode.pp.ua" class="text-decoration-none">
                https://scode.pp.ua</a
              >
            </p>

            <p class="text-center my-3">
              Дивись більше проектів:<br />
              <a href="https://dov.pp.ua"
                  target="_blank"
                  class="text-decoration-none"
                  @click="sendAction('dov.pp.ua', null, true)">
                https://dov.pp.ua</a
              >
            </p>
          </div>

          <div class="mx-auto 1pb-1">
            <a
              class="text-decoration-none text-black"
              href="https://github.com/danyshevskyi/scode-dev"
              target="blank"
            >
            </a>
          </div>

          <div class="mx-auto 1pb-2 1bb 1fs-5 t18">
            <a
              class="text-decoration-none text-black"
              href="https://github.com/danyshevskyi/scode-dev"
              target="blank"
              @click="sendAction('github', null, true)"
            >
              <div class="text-center my-3">
                Powered by laravel 12.x + Vue.js
              </div>
              <div class="text-center 1my-2">
                Scode on GitHub
              </div>
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
              @click="sendAction('feedback', null, true)"
            >
              <i class="bi bi-pen ps-1 pe-2"></i>Зворотний зв'язок
            </button>
          </div>
          <div class="mx-auto 1pb-3 1bb">
            <a
              class="text-decoration-none text-black"
              href="https://www.linkedin.com/in/danyshevskyi"
              target="blank"
              @click="sendAction('linkedin', null, true)"
            >
              <div class="text-center 1mb-4 mt-3 mb-5 t18">
                Oleksii Danyshevskyi <i class="bi bi-linkedin pe-2"></i>
              </div>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
