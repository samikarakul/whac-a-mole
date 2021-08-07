<template>
  <!-- <div id="nav">
    <router-link to="/">Home</router-link>
  </div> -->
  <router-view class="routerview" @mousedown="mousedownEvent" @mouseup="mouseUpEvent"/>
</template>

<script>
import hammer_small from './assets/hammer_small.png'
import hammer_small_rotated from './assets/hammer_small_rotated.png'

export default {
  created(){
      document.body.style.cursor = 'url("'+hammer_small+'"), default'
  },
  methods:{
    mousedownEvent(){
      document.body.style.cursor = 'url("'+hammer_small_rotated+'"), default'


    },
    mouseUpEvent(){
      document.body.style.cursor = 'url("'+hammer_small+'"), default'
    },
  }
}
</script>


<style>
body{
  background: #cfcfcf;
}
.routerview{
  border: solid 2px black;
  height: 90vh;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  /* -webkit-font-smoothing: antialiased; */
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /* padding: 50px; */
}

a {
  padding-top: 30px;
  margin: 30px;
  text-decoration-line: underline;
} 

a {
  display: block;
  font-weight: bold;
  color: #2c3e50;
}
/* 
a.router-link-exact-active {
  color: #42b983;
} */
</style>
