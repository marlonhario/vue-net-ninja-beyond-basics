<template>
    <nav>
        <header v-on:click="changeTitle">{{titleHeader}}</header>
        <ul>
            <li><router-link to="/" exact>Blog</router-link></li>
            <li><router-link to="/add" exact>Add a new Blog</router-link></li>
        </ul>
    </nav>
</template>

<script>
import {bus} from '../main'

export default {
    props: {
        titleHeader: {
            type: String
        }
    },
    data () {
        return {
            title: 'Vue Ninjas'
        }
    },
    methods: {
        changeTitle: function() {
            //this.$emit('changeTitle', 'Vue Wizards');
            this.titleHeader = 'Vue wizard bus';
            bus.$emit('titleChanged', 'Vvue Wizard bus');
        }
    }     
}
</script>

<style scoped>
    header {
        background: lightgreen;
        padding: 10px;
    }
    h1 {
        color: #222;
        text-align: center;
    }
    ul {
        list-style-type: none;
        text-align: center;
        margin: 0;
    }
    li {
        display: inline-block;
        margin: 0 10px;
    }
    a {
        color: #fff;
        text-decoration: none;
        padding: 6px 8px;
        border-radius: 10px;
    }
    nav {
        background: #444;
        padding: 14px 0;
        margin-bottom: 40px;   
    }
    .router-link-active {
        background: #eee;
        color: #444;
    }
</style>
