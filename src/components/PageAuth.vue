<script setup>
import axios from "axios";
import { computed, ref } from "vue";
import ModalScode from "../components/modal/ModalScode.vue";
import ModalController from "../components/modal/ModalController.vue";
import ModalStacker from "../components/modal/ModalStacker.vue";
import ModalScodesAll from "../components/modal/ModalScodesAll.vue";
import ModalControllerFunctions from "../components/modal/ModalControllerFunctions.vue";

const urlApi = import.meta.env.VITE_URL_API_APP;
const urlAnalytics = import.meta.env.VITE_URL_API_ANALYTICS;

const inputSearch = ref("");

const loading = ref(false);
const error = ref(false);
const success = ref(false);

const apiController = {
  url: "/controller",
  body: computed(() => ({})),
  result: "",
  repeat: false,
};

const apiScodeSearch = {
  url: "/scode_search",
  body: computed(() => ({
    scode: inputSearch.value,
  })),
  result: "",
  repeat: true,
};

const apiStacker = {
  url: "/stacker",
  body: computed(() => ({})),
  result: "",
  repeat: false,
};

const apiScodeAll = {
  url: "/scode_all",
  body: computed(() => ({})),
  result: "",
  repeat: false,
};

const apiControllerFunctions = {
  url: "/controller_functions",
  body: computed(() => ({})),
  result: "",
  repeat: false,
};

async function sendAnalytics(urlRequest, bodyRequest) {
  axios.post(urlAnalytics + "/" + urlRequest, bodyRequest).catch((error) => {
    console.log(error);
  });
}

async function getApi(apiRequest) {
  if (apiRequest.repeat == false && apiRequest.result != "") {
    loading.value = false;
    success.value = true;
  } else {
    loading.value = true;
    error.value = false;
    success.value = false;
    axios
      .post(urlApi + apiRequest.url, apiRequest.body.value)
      .catch((error) => {
        console.log(error);
      })
      .then((response) => {
        if (response.data !== null) {
          loading.value = false;
          success.value = true;
          apiRequest.result = response.data;
        } else {
          loading.value = false;
          error.value = true;
        }
      });
  }
}

sendAnalytics("open_app");
</script>

<template>
  <div
    class="container d-flex justify-content-between px-4 align-items-center mt-3"
  >
    <div class="text-center pt-2">
      <a
        href="https://dov.pp.ua/scode/"
        class="text-decoration-none text-black"
      >
        <h5>S C O D E</h5>
      </a>
    </div>

    <div class="col-auto">
      <button
        type="button"
        class="btn btn-outline-dark text-decoration-none"
        data-bs-toggle="dropdown"
        @click="sendAnalytics('menu')"
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
            @click="getApi(apiScodeAll), sendAnalytics('scode_all')"
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
            @click="getApi(apiStacker), sendAnalytics('stacker_scheme')"
          >
            <i class="bi bi-hdd-rack ps-1 pe-2"></i>Схема стекера
          </buttom>
        </li>

        <li class="dropdown-item px-0">
          <buttom
            type="buttom"
            class="btn btn-link text-decoration-none text-start text-black col-12 position-relative"
            data-bs-toggle="modal"
            data-bs-target="#ModalController"
            @click="getApi(apiController), sendAnalytics('controller_scheme')"
          >
            <i class="bi bi-cpu pe-2"></i>Схема контроллера
            <span
              class="position-absolute top-0 start-75 ms-3 translate-middle badge rounded-pill bg-danger"
            >
              Нове
            </span>
          </buttom>
        </li>

        <li class="dropdown-item px-0 mb-2">
          <buttom
            type="buttom"
            class="btn btn-link text-decoration-none text-start text-black col-12"
            data-bs-toggle="modal"
            data-bs-target="#ModalControllerFunctions"
            @click="
              getApi(apiControllerFunctions),
                sendAnalytics('controller_functions')
            "
          >
            <i class="bi bi-activity 1ps-1 pe-2"></i>Функціональні тести<br />контролера
          </buttom>
        </li>

        <li><hr class="p-0 my-0" /></li>
        <li class="dropdown-item px-0">
          <buttom
            type="buttom"
            class="btn btn-link text-decoration-none text-start text-black col-12"
            data-bs-toggle="modal"
            data-bs-target="#ModalAddDesktop"
            @click="sendAnalytics('add_desktop')"
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
            @click="sendAnalytics('about')"
          >
            <i class="bi bi-info-circle ps-1 pe-2"></i>Про додаток
          </buttom>
        </li>
        <!-- <li><hr class="p-0 my-0" /></li>
        <li class="dropdown-item px-0 mb-0">
          <a href="https://dov.pp.ua/miles" target="_blank">
            <buttom
              type="buttom"
              class="btn btn-link text-decoration-none text-start text-black col-12"
            >
              <i class="bi bi-car-front ps-1 pe-2"></i>Пробіг авто
            </buttom>
          </a>
        </li> -->
        <li><hr class="p-0 my-0" /></li>
        <li class="dropdown-item px-0 my-1">
          <a href="https://www.privat24.ua/send/i6l12" target="_blank">
            <buttom
              type="buttom"
              class="btn btn-link text-decoration-none text-start text-black col-12"
              @click="sendAnalytics('donats')"
            >
              <i class="bi bi-cup-hot ps-1 pe-2"></i>Підтримати проект
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
        @click="
          getApi(apiScodeSearch);
          sendAnalytics('scode_search', apiScodeSearch.body.value);
          inputSearch = '';
        "
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
    <!-- <img :src="coffee" alt="coffee" class="pb-2"> -->
    <!-- <i class="bi bi-cup-hot"></i>&nbspПідтримати проект -->
    <!-- &nbsp Підтримати 💙💛 -->
    <!-- </div> -->
    <!-- </a> -->
    <a
      class="text-decoration-none text-black"
      href="https://dov.pp.ua"
      target="blank"
      @click="sendAnalytics('footer')"
    >
      <div class="text-center my-2" style="font-size: 13px">
        Олексій Данишевський &copy; 2026
      </div>
    </a>
  </div>

  <ModalScode
    :apiScodeSearch="apiScodeSearch.result"
    :loading="loading"
    :error="error"
    :success="success"
  />

  <ModalController
    :apiController="apiController.result"
    :loading="loading"
    :error="error"
    :success="success"
  />

  <ModalStacker
    :apiStacker="apiStacker.result"
    :loading="loading"
    :error="error"
    :success="success"
  />

  <ModalScodesAll
    :apiScodeAll="apiScodeAll.result"
    :loading="loading"
    :error="error"
    :success="success"
  />

  <ModalControllerFunctions
    :apiData="apiControllerFunctions.result"
    :loading="loading"
    :error="error"
    :success="success"
  />
</template>
