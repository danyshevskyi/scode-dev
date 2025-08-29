<script setup>
</script>

<template>

<div class="modal fade" tabindex="-1" id="mod_about">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title"><i class="bi bi-info-circle ps-1 pe-2"></i>Про додаток</h5> 
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
  
  <div class="mt-2 px-2">
      
  <div class="container col-auto t18">
      
    <p class="mt-1 mb-0" style="text-align: justify; text-indent: 25px;">
      Scode це додаток пошуку рішень для інженерів з обслуговування банкоматів WincorNixdorf на базі контролерів CMD-V4.  
    </p>
  
    <p class="1mb-0 my-2 1bb" style="text-align: justify; text-indent: 25px;">
      По коду помилки можливо знайти опис несправностей та рішення для них.
    </p>
  
    <p class="mb-2" style="text-align: justify; text-indent: 25px;">
      <span class="fw-medium">Дозволяє ознайомитись з списоком скодів та вивчити схему стекера. </span>
    </p>
  
    <p class="text-center my-2">Web-адрес:
        <a href="https://dov.pp.ua/scode" class="text-decoration-none"> https://dov.pp.ua/scode</a> 
    </p>
  
    <p class="mb-0">
      <span class="fw-medium"><i class="bi bi-check2-circle fs-5 ps-4"></i> Technology stack:</span>
    </p>
        <ul class="mb-1 1bb">
            <li>HTML 5.0, CSS 3.0, JavaScript 3.0</li>
            <li>Vue.js + Vite, Bootstrap v.5.3</li>
            <li>laravel 12.x, PHP 8.2, MySQL, Git</li>
        </ul>
    <p class="text-center mt-3"> 
      <a href="https://github.com/danyshevskyi/scode-dev" class="text-decoration-underline text-dark" target="_blank">
          <i class="bi bi-github pe-2 1text-black"></i>Scode on GitHub
      </a>
    </p>
  
    <p class="text-center mt-3"> 
      <a href="https://dov.pp.ua" class="text-decoration-none text-dark" target="_blank">
          More projects on <span class="text-decoration-none text-primary">https://dov.pp.ua</span>
      </a>
    </p>
  </div>
  
  <div class="d-flex justify-content-center mt-4 mb-2">
      <button type="button"
              id="aboutButReg"
              class="btn btn-outline-dark rounded-5 col-11 py-2 fs-5 1px-5 text-decoration-none"
              style="margin-bottom: 13px;"
              data-bs-toggle="modal"
              data-bs-target="#ModalFeedback">
              <i class="bi bi-pen ps-1 pe-2"></i>Залишити відгук
              </button>
  </div>

  <a class="text-decoration-none text-black" href="https://www.linkedin.com/in/danyshevskyi/" target="_blank"> 
      <div class="text-center 1mt-1 mb-4" style="font-size: 13px;">Oleksii Danyshevskyi &copy; 2025    
      <i class="bi bi-linkedin"></i>
    </div>
  </a>
  
  </div>
      
      </div>
    </div>
  </div>

</template>

<style scoped>
</style>