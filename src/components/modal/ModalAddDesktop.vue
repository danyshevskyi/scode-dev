<script setup>
import shortcut_chrome_01 from '../../assets/shortcut_chrome_01.png'
import shortcut_chrome_02 from '../../assets/shortcut_chrome_02.png'
import shortcut_chrome_03 from '../../assets/shortcut_chrome_03.png'
import shortcut from '../../assets/shortcut.png'
</script>

<template>

<div class="modal fade" tabindex="-1" id="ModalAddDesktop">
  <div class="modal-dialog">
    <div class="modal-content">
      

      <div class="modal-header sticky-top" style="position: fixed8; background-color: white;">
        <h5 class="modal-title"><i class="bi bi-check2-circle pe-2 fs-3"></i>Додати на робочий стіл</h5>
        
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      

      <div class="modal-body">
    

<div class="t18">

<h5 class="text-center">Для Google Chrome<i class="bi bi-browser-chrome ps-2"></i></h5>

<p class="text-center mt-3 mb-0">1. Натисніть на три крапки у верхньому правому куті.</p>

<div class="text-center">
    <img :src="shortcut_chrome_01" alt="stacker" class="mb-4 me-4 text-center">
        </div>


<p class="text-center mt-3 mb-0">2. Оберіть "Додати на головний ек...".</p>
<div class="text-center">
    <img :src="shortcut_chrome_02" alt="stacker" class="mb-4 me-4 text-center">
        </div>

<p class="text-center mt-3 mb-0">3. Натисніть "Додати".</p>
    <div class="text-center">
        <img :src="shortcut_chrome_03" alt="stacker" class="mb-4 me-4 text-center">
            </div>

<p class="text-center mt-3 mb-0">4. Готово!</p>
    <div class="text-center">
        <img :src="shortcut" alt="stacker" class="mb-4 me-4 text-center">
            </div>
  </div>
</div>

    </div>
  </div>
</div>

</template>

<style scoped>
</style>