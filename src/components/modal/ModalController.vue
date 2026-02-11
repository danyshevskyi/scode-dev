<script setup>
import circles from "../../assets/Fidget-spinner.gif";
import controller from "../../assets/controller.png";
const props = defineProps({
  apiController: Object,
  loading: Boolean,
  error: Boolean,
  success: Boolean,
});
</script>

<template>
  <div class="modal fade" tabindex="-1" id="ModalController">
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
              :src="circles"
              alt="stacker"
              class="mb-2 1me-4 text-center 1sticky-top"
            />
          </div>
        </div>
        <!-- /loading -->
        <!-- success -->
        <div class="success" v-if="success">
          <div class="sticky-top bg-white rounded-4">
            <div class="modal-header">
              <h5 class="modal-title">
                <i class="bi bi-cpu me-2"></i>Схема контроллера
              </h5>
              <button
                type="button"
                class="btn-close me-1"
                data-bs-dismiss="modal"
                aria-label="Close"
              ></button>
            </div>
            <div class="container">
              <img
                :src="controller"
                alt="stacker"
                class="mt-3 mb-3 1me-4 text-center"
                width="100%"
              />
            </div>
          </div>
          <div class="container">
            <div
              class="rounded border mb-3"
              v-for="(item, index) in apiController"
            >
              <div class="p-2 fw-bolder">{{ item.connector }}</div>
              <div class="p-2">{{ item.description }}</div>
            </div>
          </div>
        </div>
        <!-- /success -->
      </div>
    </div>
  </div>
</template>
