<template>
  <div id="app" class="container">
    <appheader/>
    <div class="wrapper">
    <ul>
      <li v-for="(user,i) in member" :key="i">
        <div>
        <card :email="user.email"
              :name="user.name"
              :msg="user.message"
              :status="user.status"
              :id="i"/>
        </div>
      </li>
    </ul>
    </div>  
  </div>
</template>

<script>
import axios from 'axios';
import cardVue from './components/card.vue';
import navbar from './components/navbar.vue';
export default {
  data(){
    return {
      member: ''
    };
  },
  components: {
    card: cardVue,
    appheader: navbar
  },
  created() {
    axios.get("https://hack-the-mountain.firebaseio.com/hackathon.json")
    .then(res =>{
      this.member = res.data
      console.log(this.member)
    })
    .catch(error => console.log(error))
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
ul{
  list-style: none;
  width: 90%;
  margin: auto;
}
.wrapper {
  text-align: center;
}
.wrapper ul {
  display: inline-block;
  margin: 0;
  padding: 0;
  zoom:1;
  *display: inline;
}
.wrapper li {
  padding: 2px 5px;
}
</style>
