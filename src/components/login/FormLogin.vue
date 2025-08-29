<script setup>
import { ref } from "vue"
import axios from 'axios'

axios.defaults.withCredentials = true
axios.defaults.withXSRFToken = true

const baseUrl = import.meta.env.VITE_BASE_URL
const appUrl = import.meta.env.VITE_APP_URL
const apiUrl = import.meta.env.VITE_API_URL

const email = ref('')
const pass = ref('')
const rem = ref('')
const isHidden = ref(true)

async function login() { 
    axios.get(baseUrl + '/sanctum/csrf-cookie').then(response => {
      axios.post(baseUrl + '/login',
         {
            email: email.value,
            password: pass.value,
            remember: rem.value,
         }
      ).catch(error => {
            isHidden.value = false
      }).then(response => {
         localStorage.setItem('user', JSON.stringify(response.data))
         location.replace(appUrl)
        }) 
   })
}

function passShow(input) {
    let getInput = document.querySelectorAll('.' + input);
        let getEye = document.querySelector('#' + input);
            for(let i = 0; i < getInput.length; i++) {  
                    if(getInput[i].type === "password")
                    {
                        getInput[i].type = "text";
                    } 
                    else 
                    {
                        getInput[i].type = "password";
                    }
            }
                getEye.classList.toggle('bi-eye-slash');
            getEye.classList.toggle('bi-eye');
}

</script>

<template>
<div class="tab-pane fade active show" id="nav-home" role="tabpanel" aria-labelledby="nav-home-tab">
   <div class="modal-body px-4">
            
            <div class="text-center text-danger mb-2"
                 id="alertLogin"
                 :hidden="isHidden">
                 <!-- Sorry, the login or password is incorrect! -->
                 Вибачте, логін або пароль неправильний!
            </div>
<form>
<div class="mb-3">
    <label for="email" class="form-label mb-1">Email</label>
    <input
            v-model="email"
            type="email"
            class="form-control border-secondary border-opacity-50"
            id="email"
            maxlength="50"
            required>
</div>

<div class="mb-3 position-relative">
   <label for="password" class="form-label mb-1">Пароль</label>
   <input
            v-model="pass"
            type="password"
            class="form-control border-secondary border-opacity-50 inputPassLog"
            id="password"
            maxlength="50"
            required>
            
        <div class="col-2 position-absolute top-0 end-0 text-center pb-1"
             style="margin-top: 30px;" 
             @click="passShow('inputPassLog')">
             <i class="bi bi-eye fs-4 text-secondary text-center" id="inputPassLog"></i>
        </div>  
</div>

<div class="form-check mt-3">
        <input id="authRem"
               v-model="rem"
               class="form-check-input border-secondary border-opacity-50"
               type="checkbox">
               <label class="form-check-label" for="authRem">Запам'ятати мене</label>
    </div>

    <div class="text-end mt-3 py-2">
      <a href="https://dov.pp.ua/forgot-password">
         <span class="me-3 text-decoration-underline text-secondary">Забули пароль?</span>
      </a> 
      <button type="button"
                class="btn btn-dark px-5"
                @click="login">
                Вхід
        </button>
    </div>

</form>

</div>
   
    </div>


</template>

<style scoped>
</style>