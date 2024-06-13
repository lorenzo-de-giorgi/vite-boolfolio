<template>
    <h1>Contact Us</h1>
    <div class="row">
        <form @submit.prevent="sendForm()" class="col-12 text-start">
            <div class="mb-3">
                <input type="text" class="form-control border-0 border-bottom" placeholder="Name" v-model="name">
            </div>
            <div class="mb-3">
                <input type="email" class="form-control border-0 border-bottom" placeholder="Email" v-model="email">
            </div>
            <div class="mb-3">
                <label for="message">Your Message</label>
                <textarea id="message" cols="30" rows="10" class="form-control border-0 border-bottom" v-model="message">{{ message }}</textarea>
            </div>
            <button class="btn btn-lg btn-primary text-white" type="submit">Send</button>
        </form>
    </div>
</template>

<script>
import { store } from '../store.js';
import axios from 'axios'
export default {
    name: 'ContactComponent',
    data(){
        return{
            store,
            name: '',
            email: '',
            message: ''
        }
    },
    methods: {
        sendForm(){
            const data = {
                name: this.name,
                address: this.email,
                message: this.message
            }
            axios.post(`${this.store.apiBaseUrl}/contacts`, data).then((res)=>{
                // console.log(res.data.status);
            }).catch((error)=>{
                console.log(error)
            })
        }
    },
}
</script>

<style lang="scss" scoped></style>