<script setup>

import axios from 'axios'
// import { ref } from 'vue'

const appUrl = import.meta.env.VITE_APP_URL
const apiUrl = import.meta.env.VITE_API_URL

const user = JSON.parse(localStorage.getItem('user'))
// const email = ref(user.email);

function logout() {
    axios.post(apiUrl + '/logout').then(response => {  
    }).catch(error => {
        console.log(error)
    }).then(response => {
        localStorage.removeItem('user')
        location.replace(appUrl)
    })
}

</script>

<template>

<div class="container 1header d-flex justify-content-between px-4 1bb align-items-center mt-3">

<div class="text-center pt-2">
        <a href="https://dov.pp.ua/scode/" class="text-decoration-none text-black">
          <h5>SCODE for CMD-V4</h5>
        </a>
</div>

  <div class="col-auto 1bb">
       
<button type="button"
        class="btn btn-outline-dark text-decoration-none"
        data-bs-toggle = "dropdown">
        Menu
</button>    
  
        <ul class="dropdown-menu">
      <li class="dropdown-item fw-semibold" id="email">{{ email }}</li>
          <li><hr class=""></li>

          <li class="dropdown-item px-0">
                      <a class="btn btn-link text-decoration-none text-start text-black col-12"
                              href="" role="button">
                                      <i class="bi bi-person ps-1 pe-2 fs-5"></i>Profile</a>
          </li>

          <li class="dropdown-item px-0">
                  <buttom type="buttom"
                          class="btn btn-link text-decoration-none text-start text-black col-12"
                          data-bs-toggle = "modal"
                          data-bs-target = "#mod_review">
                          <i class="bi bi-pen ps-1 pe-2"></i>Contact us
                  </buttom>
              
              </li>
              <li class="dropdown-item px-0">
                  <buttom type="buttom"
                          class="btn btn-link text-decoration-none text-start text-black col-12"
                          data-bs-toggle = "modal"
                          data-bs-target = "#mod_about">
                          <i class="bi bi-info-circle ps-1 pe-2"></i>About
                  </buttom>
              </li>               

              <li><hr class="dropdown-divider"></li>
              
              <li class="dropdown-item px-0">
                            <!-- <form method="POST"> -->
                         
                            <x-dropdown-link
                                    @click="logout"
                                                class="text-decoration-none text-black ps-3">       
                               <i class="bi bi-door-open pe-1"></i>
                               Sign out
                            </x-dropdown-link>
                        <!-- </form>         -->
                </li>  
          
              <li class="dropdown-item px-0">
                        
              </li>       
      </ul>
  </div>

</div>



<div class="container d-flex align-items-center justify-content-center" style="height: 70vh;">

<div class="1bb text-center col-md-7">
   
<div class="mb-3 1bb">
  <input type="text" class="form-control text-center fs-4" id="inputScode"
  placeholder="">
  <div id="inputScode" class="form-text text-center">Введите код контроллера, например: 23</div>
</div>


<button type="button"
        class="btn btn-dark col-5 col-md-3 mt-4"
        data-bs-toggle="modal"
        data-bs-target="#mod_scod_show"
        >Пошук</button>

</div>

</div>

<!-- footer -->
<div class="mx-auto fixed-bottom pb-3" style="max-width: 1000px">
  <a class="text-decoration-none text-black" href="https://www.linkedin.com/in/danyshevskyi/" target="blank"> 
  <div class="text-center mt-3" style="font-size: 13px;">Oleksii Danyshevskyi &copy; 2024 
  <i class="bi bi-linkedin"></i>
</div>
</a>
</div>





</template>

<style scoped>
</style>