<script setup>
import { ref } from "vue"
import axios from 'axios'

axios.defaults.withCredentials = true
axios.defaults.withXSRFToken = true

const baseUrl = import.meta.env.VITE_BASE_URL
const appUrl = import.meta.env.VITE_APP_URL
const apiUrl = import.meta.env.VITE_API_URL

const name = ref('')
const email = ref('')
const pass = ref('')
const pass_confirm = ref('')

const errorEmail = ref('')
const errorName = ref('')
const errorPass = ref('')

async function register() {
   axios.get(baseUrl + '/sanctum/csrf-cookie').then(response => {
      axios.post(baseUrl+ '/register',
         {
            name: name.value,
            email: email.value,
            password: pass.value,
            password_confirmation: pass_confirm.value,
         }
      ).catch(error => {

        errorEmail.value = null
            errorName.value = null
                errorPass.value = null

        const objectErrors = error.response.data.errors

        const arrayErrors = Object.entries(objectErrors)

        arrayErrors.forEach(function(item) {           
            if(item[0] == 'name')
            {
                errorName.value = item[1][0]
            }
            else if (item[0] == 'email')
            {
                errorEmail.value= item[1][0]
            }
            else if (item[0] == 'password')
            {
                errorPass.value = item[1][0]
            }
        }        
)   
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

<div class="tab-pane fade" id="nav-profile" role="tabpanel" aria-labelledby="nav-profile-tab">

<div class="modal-body px-4">

<form>

<div class="text-center text-danger">{{ errorName }}</div>
<div class="mb-3">
    <label for="name" class="form-label mb-1">Name</label>
    <input
            v-model="name"
            type="text"
            class="form-control border-secondary border-opacity-50"
            id="name">
</div>

<div class="text-center text-danger">{{ errorEmail }}</div>
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

<div class="text-center text-danger">{{ errorPass }}</div>
<div class="mb-3 position-relative">
    <label for="password" class="form-label mb-1">Password</label>
    <input
            v-model="pass"
            type="password"
            class="form-control border-secondary border-opacity-50 inputPassReg"
            id="password"
            maxlength="50"
            required>
            
        <div class="col-2 position-absolute top-0 end-0 text-center pb-1"
             style="margin-top: 31px;" 
             @click="passShow('inputPassReg')">
             <i class="bi bi-eye fs-4 text-secondary text-center" id="inputPassReg"></i>
        </div>  
</div>

<div>
    <label for="password_confirm" class="form-label mb-1">Confirm Password</label>
    <input
            v-model="pass_confirm"
            type="password"
            class="form-control border-secondary border-opacity-50 inputPassReg"
            id="password_confirm">
</div>


<div class="form-text mt-3">
    <div id="passwordHelpBlock" class="form-text"> The password field must be at least 8 characters
    </div>
</div>



    <div class="text-end mt-3 py-2">
        <button type="button"
                class="btn btn-dark px-4"
                @click="register">
                Register
        </button>
    </div>

</form>

</div>
</div>

</template>

<style scoped>
</style>