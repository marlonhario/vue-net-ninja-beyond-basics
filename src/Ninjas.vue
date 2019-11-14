<template>
    <div id="ninjas">
        <h1>List of Ninjas</h1>
        <ul>
            <li v-for="ninja in ninjas" v-on:click="ninja.show = !ninja.show">
                <h2>{{ninja.name}}</h2>
                <h3 v-show="ninja.show">{{ninja.speciality}}</h3>
            </li>
        </ul>
        <button v-on:click="deletNinja">Delete ninja</button>    
    </div>
</template>

<script>
export default {
    //props: ['ninjas'],
    props: {
        ninjas: {
            type: Array,
            required: true
        }
    },
    data () {
        return {
        
        }
    }, 
    methods: {
        test: function() {
            this.ninjas
        },
        deletNinja: function() {
            this.ninjas.pop();
        }
    },
    //lifecycle hooks
    beforeCreate() {
        console.log('beforeCreate');
    },
    created() {
        console.log('created');
    },
    beforeMount() {
        console.log('beforeMount');
    },
    mounted() {
        console.log('mounted');
    },
    beforeUpdate() {
        console.log('beforeUpdate');
    },
    updated() {
        console.log('updated');
    }
}
</script>

<style scoped>
    h1 {
        color: green;
    }

    #ninjas {
        width: 100%;
        max-width: 1200px;
        margin: 40px auto;
        padding: 0 20px;
        box-sizing: border-box;
    }

    ul {
        display: flex;
        flex-wrap: wrap;
        list-style-type: none;
        padding: 0;
    }

    li {
        flex-grow: 1;
        flex-basis: 300px;
        text-align: center;
        padding: 30px;
        border: 1px solid #222;
        margin: 10px;
    }
</style>
