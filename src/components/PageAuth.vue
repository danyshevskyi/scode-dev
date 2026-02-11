<script setup>
import axios from "axios";
import { ref } from "vue";
import ModalScode from "../components/modal/ModalScode.vue";
import ModalController from "../components/modal/ModalController.vue";

axios.defaults.withCredentials = true;
axios.defaults.withXSRFToken = true;

const appUrl = import.meta.env.VITE_APP_URL;
const apiUrl = import.meta.env.VITE_API_URL;
const baseUrl = import.meta.env.VITE_BASE_URL;

const inputSearch = ref();
const apiSearch = ref();

const loading = ref(false);
const error = ref(false);
const success = ref(false);

const apiController = {
  url: '/controller',
  body: {},
  result: ref(),
  repeat: false
};

// const apiSearch = {
//   url: '/search',
//   body: {scode: inputScode.value},
//   result: ref(),
//   repeat: true
// };

async function getApiScode() {
  loading.value = true;
  error.value = false;
  success.value = false;

  axios
    .post(apiUrl + "/search", {
      scode: inputSearch.value,
    })
    .catch((error) => {
      console.log(error);
    })
    .then((response) => {
      if (response.data !== null) {
        loading.value = false
        success.value = true
        apiSearch.value = response.data
      } else {
        loading.value = false;
        error.value = true;
      }
    });
  inputSearch.value = null;
}

// async function scodeSearch() {
//   apiSearch.body = {scode: inputScode.value}
//     getApi(apiSearch)
    
// }

async function getApi(parameters) {  
  if (parameters.repeat == false && parameters.result.value != null) {
    loading.value = false;
    success.value = true;
  } else {
    loading.value = true;
    error.value = false;
    success.value = false;
        axios
        .post(apiUrl + parameters.url, parameters.body)
        .catch((error) => {
                console.log(error);
        })
        .then((response) => {
                if (response.data !== null) {
                loading.value = false;
                success.value = true;
                parameters.result.value = response.data;  
                console.log(success.value)  
                } else {
                loading.value = false;
                error.value = true;
                }
        });
      }
}

</script>

<template>
  <div
    class="container 1header d-flex justify-content-between px-4 1bb align-items-center mt-3"
  >
    <div class="text-center pt-2">
      <a
        href="https://dov.pp.ua/scode/"
        class="text-decoration-none text-black"
      >
        <h5>S C O D E</h5>
      </a>
    </div>

    <div class="col-auto 1bb">
      <button
        type="button"
        class="btn btn-outline-dark text-decoration-none"
        data-bs-toggle="dropdown"
      >
        Меню
      </button>

      <ul class="dropdown-menu py-0">
        <!-- <li class="dropdown-item fw-semibold py-2 my-1" id="email">{{ user.email }}</li>
        <li><hr class="p-0 my-0"></li> -->
        <li class="dropdown-item px-0 1bb mt-1">
          <buttom
            type="buttom"
            class="btn btn-link text-decoration-none text-start text-black col-12"
            data-bs-toggle="modal"
            data-bs-target="#ModalScodesAll"
          >
            <i class="bi bi-book ps-1 pe-2"></i>Всі скоди
          </buttom>
        </li>
        <li class="dropdown-item px-0">
          <buttom
            type="buttom"
            class="btn btn-link text-decoration-none text-start text-black col-12"
            data-bs-toggle="modal"
            data-bs-target="#ModalStacker"
          >
            <i class="bi bi-hdd-rack ps-1 pe-2"></i>Схема стекера
          </buttom>
        </li>
        <li class="dropdown-item px-0 mb-2">
          <buttom
            type="buttom"
            class="btn btn-link text-decoration-none text-start text-black col-12"
            data-bs-toggle="modal"
            data-bs-target="#ModalController"
            @click="getApi(apiController)"
          >
            <i class="bi bi-cpu pe-2"></i>Схема контроллера
          </buttom>
        </li>
        <li><hr class="p-0 my-0" /></li>
        <li class="dropdown-item px-0">
          <buttom
            type="buttom"
            class="btn btn-link text-decoration-none text-start text-black col-12"
            data-bs-toggle="modal"
            data-bs-target="#ModalFeedback"
          >
            <i class="bi bi-pen ps-1 pe-2"></i>Зворотний зв'язок
          </buttom>
        </li>
        <li class="dropdown-item px-0 mb-2">
          <buttom
            type="buttom"
            class="btn btn-link text-decoration-none text-start text-black col-12"
            data-bs-toggle="modal"
            data-bs-target="#ModalAddDesktop"
          >
            <i class="bi bi-box-arrow-in-down-left ps-1 pe-2"></i>Додати на
            робочий стіл
          </buttom>
        </li>
        <li class="dropdown-item px-0 mb-2">
          <buttom
            type="buttom"
            class="btn btn-link text-decoration-none text-start text-black col-12"
            data-bs-toggle="modal"
            data-bs-target="#mod_about"
          >
            <i class="bi bi-info-circle ps-1 pe-2"></i>Про додаток
          </buttom>
        </li>
        <li><hr class="p-0 my-0" /></li>
        <li class="dropdown-item px-0 mb-0">
          <a href="https://dov.pp.ua/miles" target="_blank">
            <buttom
              type="buttom"
              class="btn btn-link text-decoration-none text-start text-black col-12"
            >
              <i class="bi bi-car-front ps-1 pe-2"></i>Пробіг авто
            </buttom>
          </a>
        </li>
      </ul>
    </div>
  </div>

  <!-- Body -->
  <div
    class="1bb container d-flex align-items-center justify-content-center"
    style="height: 75vh"
  >
    <div class="1bb text-center col-md-7 1mt-5">
      <div class="mb-3 1bb">
        <form autocomplete="off" @submit.prevent="handleSubmit">
          <input
            type="text"
            autocomplete="off"
            class="form-control text-center fs-4"
            id="inputScode"
            placeholder=""
            v-model="inputSearch"
          />
        </form>
        <div class="form-text text-center">
          Введіть код контролера, наприклад: 20
        </div>
      </div>
      <button
        type="button"
        class="btn btn-dark col-5 col-md-3 1mt-4 mb-5"
        data-bs-toggle="modal"
        data-bs-target="#ModalScode"
        @click="getApiScode()"
        ref="q"
      >
        Пошук
      </button>
    </div>
  </div>

  <!-- Footer -->
  <div class="mx-auto fixed-bottom pb-3" style="max-width: 1000px">
    <!-- <a
      class="text-decoration-none text-black"
      href="https://www.privat24.ua/send/i6l12"
      target="blank"
    > -->
      <!-- <div class="text-center py-1"> -->
        <!-- <img :src="coffee" alt="coffee" class="pb-2" width="5%">&nbspСказати дякую -->
        <!-- &nbsp Підтримати 💙💛
      </div> -->
    <!-- </a> -->
    <!-- <a class="text-decoration-none text-black" href="https://dov.pp.ua" target="blank"> -->
    <div class="text-center mt-2" style="font-size: 13px">
      Олексій Данишевський &copy; 2026
    </div>
    <!-- </a> -->
  </div>

  <ModalScode
    :apiSearch="apiSearch"
    :loading="loading"
    :error="error"
    :success="success"
  />

  <ModalController
    :apiController="apiController.result.value"
    :loading="loading"
    :error="error"
    :success="success"
  />
</template>
