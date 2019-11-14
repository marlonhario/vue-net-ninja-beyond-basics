<template>
    <div v-theme:column="'narrow'" id="show-blogs">
       <h1>All blog articles</h1>
       <input type="text" v-model="search" placeholder="search blogs" />
       <div v-for="blog in filteredBlogs" class="single-blog">
           <router-link v-bind:to="'/blog/' + blog.id"><h2 v-rainbow>{{blog.title | to-uppercase}}</h2></router-link>
           <article>{{blog.content | snippet}}</article>
       </div>
    </div>    
</template>

<script>
import searchMixin from '../mixins/searchMixin';

export default {
   
    data () {
        return {
            blogs: [],
            search: ''
        }
    },
    method: {

    },
    created() {
        this.$http.get('https://vue-net-ninja-7f930.firebaseio.com/posts.json').then(function(data) {
            // console.log(data);
            return data.json();
            // this.blogs = data.body.slice(0, 5);
        }).then(function(data){
            var blogsArray = [];

            for (let key in data) {
                // console.log(data[key]);
                data[key].id = key;
                blogsArray.push(data[key]);
            }

            this.blogs = blogsArray; 
            // console.log(data);
            // console.log(blogsArray);
        })
    },
    computed: {
        //filteredBlogs: function() {
        //    return this.blogs.filter((blog) => {
        //        return blog.title.match(this.search);
        //    });
        //}
    },
    filters: {
        toUppercase (value){
            return value.toUpperCase();
        }
        //'to-uppercase', function(value){
        //    return value.toUpperCase();
        //}
    },
    directives: {
        'rainbow': {
            bind(el, binding, vnode) {
                el.style.color = "#" + Math.random().toString(16).slice(2,8);
            }
        }
    },
    mixins: [searchMixin]  
}
</script>

<style scoped>
   #show-blogs {
       max-width: 800px;
       margin: 0 auto;
   }
    .single-blog {
        padding: 20px;
        margin: 20px 0;
        box-sizing: border-box;
        background: #eee;
    }
</style>
