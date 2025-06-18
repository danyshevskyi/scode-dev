<script setup>
import { ref } from 'vue'
import PageAuth from './components/PageAuth.vue'
import PageNotAuth from './components/PageNotAuth.vue'
import ModalAbout from './components/modal/ModalAbout.vue'
// import ModalLogin from './components/modal/ModalLogin.vue'
import ModalScode from './components/modal/ModalScode.vue'
import ModalLogin from './components/login/ModalLogin.vue'

const user = JSON.parse(localStorage.getItem('user'))
  
   let auth = ref(false)
      if (user !== null) {
         auth = ref(true)
      }

</script>

<template>

<PageAuth v-if=auth></PageAuth>
<PageNotAuth v-else></PageNotAuth>



<div>{{ }}</div>

<ModalAbout />
<ModalLogin />
<!-- <ModalScode /> -->

</template>

<style scoped>

</style>
