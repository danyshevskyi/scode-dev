<script setup>
import { ref } from "vue"
import axios from 'axios'
import FormRegister from './FormRegister.vue'
import FormLogin from './FormLogin.vue'

const isActiveSignIn = ref('')
const isActiveReg = ref('')


</script>

<template>
<div class="modal fade" tabindex="-1" id="mod_entry">
    
  <div class="modal-dialog">
    <div class="modal-content">

<!------------------- navigation ------------------->
<div class="nav nav-tabs pt-3 mb-2 border-secondary border-opacity-50" id="nav-tab" role="tablist">

    <button class="nav-link but_tab_reg text-dark active"
            id="nav-home-tab"
            data-bs-toggle="tab"
            data-bs-target="#nav-home"
            type="button"
            role="tab"
            aria-controls="nav-home"
            aria-selected="true">
            Вхід
    </button>
    
    <button class="nav-link text-dark"
            id="nav-profile-tab"
            data-bs-toggle="tab"
            data-bs-target="#nav-profile"
            type="button"
            role="tab"
            aria-controls="nav-profile"
            aria-selected="false">
            Реєстрація
    </button>

    <button type="button"
            class="btn-close t18 me-3 ms-auto"
            data-bs-dismiss="modal"
            aria-label="Close">
    </button>
    
</div>
<!------------------- /navigation ------------------->

        <div class="tab-content" id="nav-tabContent">
            <FormLogin />
            <FormRegister />
        </div>
        
    </div>
    </div>
</div>
</template>

<style scoped>
</style>