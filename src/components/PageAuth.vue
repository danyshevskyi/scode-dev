<script setup>

import axios from 'axios'
import { ref } from 'vue'
import ModalScode from '../components/modal/ModalScode.vue'

axios.defaults.withCredentials = true
axios.defaults.withXSRFToken = true

const appUrl = import.meta.env.VITE_APP_URL
const apiUrl = import.meta.env.VITE_API_URL
const baseUrl = import.meta.env.VITE_BASE_URL

const user = ref(JSON.parse(localStorage.getItem('user')))

const scodeSearch = ref('')
const jsonEmptyTemplate = ref(
        {
                data: {
                        status: "",
                        scode: null,
                        error: "Вказаний scode не знайдений",
                        solution: "Переглянути список scode можна в меню \"всі скоди\""
                }
        }
)

const resultApiScode = ref()
resultApiScode.value = jsonEmptyTemplate.value

async function getApiScode() {

        

        axios.post(apiUrl + '/scode',
                        {
                        'scode' : scodeSearch.value
                        }
                )
                .catch(error => {
                        console.log(error)
                })
                .then(response => {
                        console.log(response.data)
                        
                        if(response.data.status == true) {
                                resultApiScode.value = response.data

                                console.log('true')
                        } else {
                                console.log('false')
                                resultApiScode.value = jsonEmptyTemplate.value

                                console.log(resultApiScode)
                        }

                        
                })
                
                scodeSearch.value = null

        }




function searchScode() {

        getApiScode();

}

function logout() {
    axios.post(baseUrl + '/logout').then(response => {  
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

<ul class="dropdown-menu py-0">
        <li class="dropdown-item fw-semibold py-2 my-1" id="email">{{ user.email }}</li>
        <li><hr class="p-0 my-0"></li>
        <li class="dropdown-item px-0 1bb mt-1">
                <buttom type="buttom"
                        class="btn btn-link text-decoration-none text-start text-black col-12"
                        data-bs-toggle = "modal"
                        data-bs-target = "#ModalScodesAll">
                        <i class="bi bi-book ps-1 pe-2"></i>Всі скоди
                </buttom>  
        </li>
        <li class="dropdown-item px-0">
                <buttom type="buttom"
                        class="btn btn-link text-decoration-none text-start text-black col-12"
                        data-bs-toggle = "modal"
                        data-bs-target = "#ModalFeedback">
                        <i class="bi bi-pen ps-1 pe-2"></i>Залишити відгук
                </buttom>
        </li>
        <li class="dropdown-item px-0 mb-2">
                <buttom type="buttom"
                        class="btn btn-link text-decoration-none text-start text-black col-12"
                        data-bs-toggle = "modal"
                        data-bs-target = "#mod_about">
                        <i class="bi bi-info-circle ps-1 pe-2"></i>Про додаток
                </buttom>
        </li>               
        <li><hr class="p-0 my-0"></li>
        <li class="dropdown-item px-0 my-0 1bb">
                <buttom type="buttom"
                        class="btn btn-link text-decoration-none text-start text-black col-12"
                        @click="logout">
                        <i class="bi bi-info-circle ps-1 pe-2"></i>Вихід
                </buttom>
        </li>  
</ul>

</div>
</div>



<div class="container d-flex align-items-center justify-content-center" style="height: 75vh;">

<div class="1bb text-center col-md-7 mt-5">
   
<div class="mb-3 1bb">

<form autocomplete="off">
<input type="text"
        autocomplete="off"
        class="form-control text-center fs-4" id="inputScode"
        placeholder=""
        v-model="scodeSearch">
</form>

  <div class="form-text text-center">Введите код контроллера, например: 23</div>
</div>

<button type="button"
        class="btn btn-dark col-5 col-md-3 1mt-4 mb-5"
        data-bs-toggle="modal"
        data-bs-target="#ModalScode"
        @click="searchScode">Пошук
</button>
    
</div>
</div>


<!-- footer -->
<div class="mx-auto fixed-bottom pb-3" style="max-width: 1000px">
  <a class="text-decoration-none text-black" href="https://www.linkedin.com/in/danyshevskyi/" target="blank"> 
  <div class="text-center mt-3" style="font-size: 13px;">Oleksii Danyshevskyi &copy; 2025 
  <i class="bi bi-linkedin"></i>
</div>
</a>
</div>


<ModalScode :resultApiScode="resultApiScode" />


</template>
<style scoped>
</style>