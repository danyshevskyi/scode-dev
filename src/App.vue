<script setup>
import { ref } from 'vue'
import PageAuth from './components/PageAuth.vue'
import PageNotAuth from './components/PageNotAuth.vue'
import ModalAbout from './components/modal/ModalAbout.vue'
import ModalLogin from './components/modal/ModalAuth.vue'
import axios from 'axios'



// const token = "eyJpdiI6Inh6bFZKTkNQWXc4YUJTd3Vua3BWV2c9PSIsInZhbHVlIjoidjgxT2pVOFpkQ08vdjBzL24xNXJBb3B4Mm8rTWFweEpERHBBSGZVWEJDMzZEQllkRzhVRTFrSlhWUFVnQnd1SEo0RXNUZlBuM21NczdIdHpXdzlQYzN1cGRZTHhlcVNEdndnQmo4QVVCTGxScW1tcktFaDZ2MElxVnE1UDdDVVQiLCJtYWMiOiJiYmI0ZmMyN2FmMjFjYzI0ZjM2ZDE5NGZmYjgwNDAxMTkwOTBhNDRkZDgzMWJjZmVjZmRiZGJlODFhZTI5NTk3IiwidGFnIjoiIn0"

// const body = {
//     "name": "Axios",
//     "email": "axios@gmail.com",
//     "password": "12345678"
// }

// const header = {
//     "Accept": "application/json",
//     "X-XSRF-TOKEN": token
// }



async function sentFetch() {
    const sss = await fetch (
                    'http://127.0.0.1:8000/api/reg',
                    {
                        method: 'POST',  
                        headers:
                                {
                        'Accept': 'application/json',
                        'X-XSRF-TOKEN':            'eyJpdiI6Inh6bFZKTkNQWXc4YUJTd3Vua3BWV2c9PSIsInZhbHVlIjoidjgxT2pVOFpkQ08vdjBzL24xNXJBb3B4Mm8rTWFweEpERHBBSGZVWEJDMzZEQllkRzhVRTFrSlhWUFVnQnd1SEo0RXNUZlBuM21NczdIdHpXdzlQYzN1cGRZTHhlcVNEdndnQmo4QVVCTGxScW1tcktFaDZ2MElxVnE1UDdDVVQiLCJtYWMiOiJiYmI0ZmMyN2FmMjFjYzI0ZjM2ZDE5NGZmYjgwNDAxMTkwOTBhNDRkZDgzMWJjZmVjZmRiZGJlODFhZTI5NTk3IiwidGFnIjoiIn0'
                                },
                        body: JSON.stringify(      {  name: "Axios",
        email: "axios4@gmail.com",
        password: "12345678"
                    }).then(sss.json())
                    }
                );
                    // const result = await response.json();

                    // return sss;
}




function sentData() {

    return axios.post(
    'http://127.0.0.1:8000/api/reg',
    {
        name: "Axios",
        email: "axios4@gmail.com",
        password: "12345678"
    },
    {
    headers: {
                        'Accept': 'application/json',
                        'X-XSRF-TOKEN':            'eyJpdiI6Inh6bFZKTkNQWXc4YUJTd3Vua3BWV2c9PSIsInZhbHVlIjoidjgxT2pVOFpkQ08vdjBzL24xNXJBb3B4Mm8rTWFweEpERHBBSGZVWEJDMzZEQllkRzhVRTFrSlhWUFVnQnd1SEo0RXNUZlBuM21NczdIdHpXdzlQYzN1cGRZTHhlcVNEdndnQmo4QVVCTGxScW1tcktFaDZ2MElxVnE1UDdDVVQiLCJtYWMiOiJiYmI0ZmMyN2FmMjFjYzI0ZjM2ZDE5NGZmYjgwNDAxMTkwOTBhNDRkZDgzMWJjZmVjZmRiZGJlODFhZTI5NTk3IiwidGFnIjoiIn0'
                    }
    }

)
.then(response => {
    console.log(response.data);
})
.catch(error => {
      console.error(error.response.data.message);
    //   const qqq = ref(error.response.data.message);
    // return 'a';
})

// return console.error(error.response.data.message);

}



console.log(sentFetch());

// const auth = false;

// if(sentData) {
    
// } else {
//     const auth = ref(false)
// }



// console.log(sentData());

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
