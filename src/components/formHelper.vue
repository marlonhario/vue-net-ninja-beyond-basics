<template>
    <div>
        <slot name="title"></slot> 
        <h1> 
            I am form helper   
        </h1>   
        <slot name="text"></slot> 

        <h1>Please fill out our form...</h1>
        <form>
            <div id="form-header">
                <slot name="form-header"></slot>
            </div>
            <div id="form-fields">
                <slot name="form-fields"></slot>
            </div>
            <div id="form-controls">
                <slot name="form-controls"></slot>
            </div>
            <div id="useful-links">
                <ul>
                    <li><a href="#">Link 1</a></li>
                    <li><a href="#">Link 2</a></li>
                    <li><a href="#">Link 3</a></li>
                    <li><a href="#">Link 4</a></li>
                </ul>
            </div>
        </form>
    </div>    
</template>

<script>
export default {
   
    data () {
        return {
        }
    }  
}
</script>

<style scoped>
   
</style>
