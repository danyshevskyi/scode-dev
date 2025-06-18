<script setup>
import { ref } from "vue"
import axios from 'axios'

// axios.defaults.withCredentials = true
// axios.defaults.withXSRFToken = true

const baseUrl = import.meta.env.VITE_BASE_URL
const appUrl = import.meta.env.VITE_APP_URL
const apiUrl = import.meta.env.VITE_API_URL

const name = ref('')
const email = ref('')
const pass = ref('')
const pass_confirm = ref('')

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
         console.log(error)
      }).then(response => {
         localStorage.setItem('user', JSON.stringify(response.data))
         location.replace(appUrl)
        })
   })
}

</script>

<template>

<div class="tab-pane fade" id="nav-profile" role="tabpanel" aria-labelledby="nav-profile-tab">

<!-- <form method="POST" id="formReg"> 
    <input name="keyPOST" value="reg" _id="auth" hidden>      -->

<div class="modal-body px-4">

<div id="wrongLogin" class="text-center text-danger mb-3" style="display: none;"></div>

<form>

<div class="mb-3">
    <label for="name" class="form-label">Name</label>
    <input
            v-model="name"
            type="text"
            class="form-control border-secondary border-opacity-50"
            id="name">
</div>

<div class="mb-3">
    <label for="email" class="form-label">Email</label>
    <input
            v-model="email"
            type="email"
            class="form-control border-secondary border-opacity-50"
            id="email"
            maxlength="50"
            required>
</div>


<div class="mb-3 position-relative">
    <label for="password" class="form-label">Password</label>
    <input
            v-model="pass"
            type="password"
            class="form-control border-secondary border-opacity-50"
            id="password"
            maxlength="50"
            required>
            
        <div class="col-2 position-absolute top-0 end-0 text-center pb-1"
             style="margin-top: 34px;" 
             onclick="passShow('inputPassAuth')">
             <i class="bi bi-eye fs-4 text-secondary text-center" id="inputPassAuth"></i>
        </div>  
</div>

<div>
    <label for="password_confirm" class="form-label">Confirm Password</label>
    <input
            type="password"
            class="form-control border-secondary border-opacity-50"
            id="password_confirm">
</div>


<div class="form-text mt-3">
    <div id="passwordHelpBlock" class="form-text"> Your password must be 8-20 characters long, contain letters and numbers, and must not contain spaces, special characters, or emoji.
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