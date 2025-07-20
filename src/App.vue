<script setup>
import { ref } from 'vue'
import PageAuth from './components/PageAuth.vue'
import PageNotAuth from './components/PageNotAuth.vue'
import ModalAbout from './components/modal/ModalAbout.vue'
import ModalLogin from './components/login/ModalLogin.vue'
import ModalScodesAll from './components/modal/ModalScodesAll.vue'
import ModalFeedback from './components/modal/ModalFeedback.vue'

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
<ModalScodesAll />
<ModalFeedback />

</template>

<style scoped>

</style>
