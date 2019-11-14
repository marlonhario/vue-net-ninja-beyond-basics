<template>
    <div>
        <form-helper>
            <div slot="form-header">
                <h3>Form One - Contact Us</h3>
                <p>Fill in this form to contact us</p>
            </div>
            <div slot="form-fields">
                <input type="text" placeholder="name" required />
                <label>Your Message:</label>
                <textarea></textarea>
            </div>
            <div slot="form-controls">
                <button v-on:click="sendSubmit">Send</button>
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
        }
    },
    methods: {
        sendSubmit: function() {
            alert('thanks for logging in form one');
        }
    }  
}
</script>

<style scoped>
   
</style>
