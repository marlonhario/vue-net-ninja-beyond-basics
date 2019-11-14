<template>
  <div>
    <div id="rowcont">
      <div id="cont">
        <br>====================================<br>
        <h1>Nesting components</h1>
        <h1>{{title}}</h1>
        <p>{{greeting()}}</p>
        <ninjas v-bind:ninjas="ninjas"></ninjas>
      </div>
      <div id="cont">
        <br>====================================<br>
        <h1>More Nesting components, Primitive and Reference, Props, Events, Event bus, Lifecycle hooks</h1>
        <app-header v-bind:titleHeader="titleHeader" v-on:changeTitle="updateTitle($event)"></app-header>
        <div style="display: flex">
          <ninjas v-bind:ninjas="ninjas"></ninjas>
          <ninjas v-bind:ninjas="ninjas"></ninjas>
        </div>
        <app-footer v-bind:titleHeader="titleHeader"></app-footer>
      </div>
    </div>

    <div id="rowcont">
      <div id="cont"> 
        <br>====================================<br>
        <h1>Slots</h1>
        <form-helper>
          <h2 slot="title">{{slotTitle}}</h2>
          <p slot="text">I am the paragraph text for the slot</p>

          <div slot="form-header">
            <h3>This is the title of the form</h3>
            <p>Information about the form</p>
          </div>
          <div slot="form-fields">
            <input type="text" placeholder="name" requried />
            <input type="password" placeholder="password" requried />
          </div>
          <div slot="form-controls">
            <button>Submit</button>
          </div>
        </form-helper>
      </div>
      <div id="cont">
        <br>====================================<br>
        <h1>Dynamic components</h1>
        <keep-alive>
          <component v-bind:is="component"></component>
        </keep-alive>
          <button v-on:click="component = 'form-one'">Show form one</button>
          <button v-on:click="component = 'form-two'">Show form two</button>
      </div>
    </div>
    

    <div id="rowcont">
      <div id="cont"> 
        <br>====================================<br>
        <h1>Input Binding, Checkbox Binding, 
          Select Box Binding, http request, 
          get request, Custom directives, Filters, 
          CUstom Search Box(using computed property), 
          Register locally(filters and directives, 
          Mixin, Router, Hash Vs History, Router Links,
          Route Paramaeters, Posting to firebase, Retrieving post form firebase</h1>
        <app-header></app-header>  
        <add-blog></add-blog>
        <router-view></router-view>
        <list-blogs></list-blogs>
      </div>
      <div id="cont"> 
        <br>====================================<br>
        <h1>Input Binding</h1>
      </div>
    </div>
  </div>
</template>

<script>

//local components
import Ninjas from './Ninjas.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import formHelper from './components/formHelper.vue'
import formOne from './components/formOne.vue'
import formTwo from './components/formTwo.vue'
import addBlog from './components/addBlog.vue'
import showBlogs from './components/showBlogs.vue'
import listBlogs from './components/listBlogs.vue'

export default {
  components: {
    'ninjas': Ninjas,
    'app-header': Header,  
    'app-footer': Footer,
    'form-helper': formHelper,
    'form-one' : formOne,
    'form-two' : formTwo,
    'add-blog' : addBlog,
    'show-blogs' : showBlogs,
    'list-blogs' : listBlogs
  },
  data () {
    return {
      title: 'Ninja App',
      titleHeader: 'Vue Ninjas from app',
      slotTitle: 'I am a dynamic slot title',
      ninjas: [
        {name: 'Ryu', speciality: 'Vue Components', show: false},
        {name: 'Crystal', speciality: 'HTML Wizardy', show: false},
        {name: 'Hitoshi', speciality: 'Click events', show: false},
        {name: 'Tango', speciality: 'Conditionals', show: false},
        {name: 'Kami', speciality: 'Webpack', show: false},
        {name: 'Yoshi', speciality: 'Data Diggin', show: false}
      ],
      component: 'form-one'
    }
  },
  methods: {
    greeting: function() {
      return 'heey cowboy';
    },
    updateTitle: function(updatedTitle) {
      this.titleHeader = updatedTitle
    }
  }
}
</script>



<style scoped>
  h1 {
    color: purple;
  }
</style>
<style>
#cont {
    border: 1px solid grey; 
    width: 600px; 
    padding: 20px; 
    overflow: scroll;
    margin-bottom: 20px;
}

#rowcont {
    display: flex; 
    justify-content: space-around;
}

</style>