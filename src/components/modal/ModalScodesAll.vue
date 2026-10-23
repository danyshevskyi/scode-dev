<script setup>
import img_loading from "../../assets/img_loading.gif";

const props = defineProps({
  apiScodeAll: Object,
  loading: Boolean,
  error: Boolean,
  success: Boolean,
});
</script>

<template>
  <div class="modal fade" tabindex="-1" id="ModalScodesAll">
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
              <i class="bi bi-book me-2"></i>Перегляд всіх скодів
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
              <div
                class="rounded border mb-3"
                v-for="(item, index) in apiScodeAll"
              >
                <div class="p-2 fw-bolder">Scode {{ item.scode }}</div>
                <div class="p-2">{{ item.error }}</div>
                <div class="p-2">{{ item.solution }}</div>
              </div>
            </div>
          </div>
        </div>
        <!-- /success -->
      </div>
    </div>
  </div>
</template>
