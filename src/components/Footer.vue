<template>
    <footer>
        <p>{{copyright}} {{titleHeader}}</p>
    </footer>
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
            copyright: 'Copyright 2017'
        }
    },
    created() {
        bus.$on('titleChanged', (data) => {
            this.titleHeader = data;
        })
    }     
}
</script>

<style scoped>
    footer {
        background: #222;
        padding: 6px;
    }

    p{
        color: lightgreen;
        text-align: center; 
    }
</style>
