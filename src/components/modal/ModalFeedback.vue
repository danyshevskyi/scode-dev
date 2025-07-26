<script setup>

import { ref } from 'vue'
import axios from 'axios'

const baseUrl = import.meta.env.VITE_BASE_URL
const apiUrl = import.meta.env.VITE_API_URL

const project = ref(2)
const textFeedback = ref('')
const user = ref(JSON.parse(localStorage.getItem('user')))

const vTextarea = ref(true)
const vOk = ref(false)

function sendFeedback() {

    vTextarea.value = !vTextarea.value
        vOk.value = !vOk.value
    
    axios.post(apiUrl + '/feedback',
         {
            project_id: project.value,
            user_id: user.value.id,
            feedback_text: textFeedback.value
         }
      ).catch(error => {
          
      }).then(response => {

    })
}

function toggle() {
    setTimeout(
                function(){
                    vTextarea.value = !vTextarea.value
                    vOk.value = !vOk.value 
                }, 200
    )
}

</script>

<template>

<div class="modal fade" tabindex="-1" id="ModalFeedback">
    
<div class="modal-dialog" v-if="vTextarea">
    <div class="modal-content">

    <div class="modal-header">  
        <h5 class="modal-title"><i class="bi bi-pencil-square pe-2"></i>Залишити відгук</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
    </div>

    <div class="modal-body">
            <div>
                <textarea class="form-control"
                        id="message"
                        rows="5"
                        placeholder=""
                        maxlength="1000"
                        v-model="textFeedback">
                </textarea>
            </div>      
    </div>
    
    <div class="modal-footer">
        <button type="button" class="btn btn-primary" @click="sendFeedback()">Відправити</button>
    </div>

    </div>

</div> 

<div class="alert alert-success" v-if="vOk">
        <div class="modal-header">  
            <h5 class="modal-title text-center col-11">Дякуємо! Відправлено успішно!</h5>
                <button type="button"
                        class="btn-close col-1"
                        data-bs-dismiss="modal"
                        aria-label="Close"
                        @click="toggle()">
                </button>
             
        </div>
</div>

</div>

</template>