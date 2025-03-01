<script setup>
import { ref } from 'vue'
import PageAuth from './components/PageAuth.vue'
import PageNotAuth from './components/PageNotAuth.vue'
import ModalAbout from './components/modal/ModalAbout.vue'
import ModalLogin from './components/modal/ModalAuth.vue'
import axios from 'axios'

axios.defaults.withCredentials = true;
axios.defaults.withXSRFToken = true;

// const credentials = {
//     "name": "Alex",
//     "email": "alex@gmail.com",
//     "password": "12345678"
// }

async function register() {
   axios.get('http://localhost:8000/sanctum/csrf-cookie').then(response => {
      axios.post("http://localhost:8000/register",
         {
            name: "Alex4",
            email: "alex4@gmail.com",
            password: "12345678",
            password_confirmation: "12345678"
         }
      ).catch(error => {
         console.log(error)
      })
   })
}

register();

</script>

<template>

<PageAuth v-if="false"></PageAuth>
<PageNotAuth v-else></PageNotAuth>



<div>{{ }}</div>

<ModalAbout />
<ModalLogin />

</template>

<style scoped>

</style>
