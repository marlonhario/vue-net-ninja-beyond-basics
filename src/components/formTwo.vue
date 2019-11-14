<template>
    <div>
        <form-helper>
            <div slot="form-header">
                <h3>Form Two - Login</h3>
                <p>Enter your details login</p>
            </div>
            <div slot="form-fields">
                <input type="text" placeholder="username" required />
                <input type="password" placeholder="password" required />
            </div>
            <div slot="form-controls">
                <button v-on:click="loginSubmit">Login</button>
            </div>
        </form-helper>
    </div>
</template>

<script>
import formHandler from './formHelper.vue'

export default {
    components: {
        'form-helper': formHandler
    },
    data () {
        return {
            counter: 0
        }
    },
    methods: {
        loginSubmit: function() {
            alert('thanks for logging in form two');
        }
    }   
}
</script>

<style scoped>
   
</style>
