<script setup>
import img_loading from "../../assets/img_loading.gif";

const apiUrl = import.meta.env.VITE_API_URL;

const props = defineProps({
  apiData: Object,
  loading: Boolean,
  error: Boolean,
  success: Boolean,
});
</script>

<template>
  <div class="modal fade" tabindex="-1" id="ModalControllerFunctions">
    <div class="modal-dialog">
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
        <!-- /loading -->
        <!-- success -->
        <div class="success" v-if="success">
          <div class="modal-header sticky-top bg-white">
            <h5 class="modal-title">
              <i class="bi bi-activity me-2"></i>Функціональні тести контролера
            </h5>
            <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="mt-2 px-1">
            <div class="container col-auto pt-2">
              <div class="mx-1 mb-4 fst-italic">
                <i class="bi bi-exclamation-circle pe-2"></i>Функції обираються
                утриманням кнопки на контролері та можуть відрізнятися залежно
                від версії прошивки.
              </div>
              <div class="rounded border mb-3" v-for="(item, index) in apiData">
                <div class="p-2 fw-bolder">Функція {{ item.function }}</div>
                <div class="p-2">{{ item.name }}</div>
                <div class="p-2">{{ item.description }}</div>
              </div>
            </div>
          </div>
        </div>
        <!-- /success -->
      </div>
    </div>
  </div>
</template>
