<script setup>
</script>

<template>

<div class="modal fade" tabindex="-1" id="mod_about">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title"><i class="bi bi-info-circle ps-1 pe-2"></i>About</h5> 
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
  
  <div class="mt-2 px-2">
      
  <div class="container col-auto t18">
      
    <p class="mt-1 mb-0" style="text-align: justify; text-indent: 10px;">
      <span class="fw-medium"><i class="bi bi-copy pe-1"></i>Scode</span> це додаток пошуку рішень для інженерів з обслуговування банкоматів WincorNixdorf на базі контролерів CMD-V4.  
    </p>
  
    <p class="1mb-0 my-2 1bb" style="text-align: justify; text-indent: 25px;">
      
      <span class="fw-medium">Дозволяє</span>, знаходити опис та рішення несправностей по коду помилки контролера з відображенням схеми диспенсора. Також є довідник всіх скодів, описів та рішень.
  
    </p>
  
    <p class="mb-2" style="text-align: justify; text-indent: 25px;">
      <span class="fw-medium">Якщо ви маєте досвіт з обслуговування банкоматів, надсилайте свої рішення по певним скодам й ми зробимо найкращі практики.</span>
    </p>
  
    <p class="text-center">
        <a href="https://dov.pp.ua/english-cards" class="text-decoration-none">https://dov.pp.ua/scod</a> 
    </p>
  
    <p class="b1b mb-0">
      <span class="fw-medium"><i class="bi bi-check2-circle fs-5 ps-4"></i> Technology stack:</span>
    </p>
        <ul class="mb-1 1bb">
            <li>HTML 5.0, CSS 3.0, JavaScript 3.0</li>
            <li>Bootstrap v.5.3, jQuery 3.7.1</li>
            <li>PHP 8.2 (MVC, Eloquent ORM, Twig)</li>
            <li>MySQL</li>
        </ul>
    <p class="text-center mt-3"> 
      <a href="https://github.com/danyshevskyi/english-cards" class="text-decoration-underline text-dark" target="_blank">
          <i class="bi bi-github pe-1 1text-black"></i>English Cards on GitHub
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
              class="btn btn-outline-primary rounded-5 col-11 py-2 fs-5 1px-5 text-decoration-none"
              style="margin-bottom: 13px;"
              data-bs-toggle="modal"
              data-bs-target="#mod_entry"
              onclick="pressReg()">Registration</button>
  </div>
  
  <a class="text-decoration-none text-black" href="https://www.linkedin.com/in/danyshevskyi/" target="_blank"> 
      <div class="text-center 1mt-1 mb-4" style="font-size: 13px;">Oleksii Danyshevskyi &copy; 2024    
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