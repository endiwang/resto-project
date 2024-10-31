<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
   
   <!-- <SignUp /> -->
    <router-view></router-view>
</template>

<script>
// import router from './routers';

// import HelloWorld from './components/HelloWorld.vue'
// import SignUp from './components/SignUp.vue';

export default {
  name: 'App',
  // components: {
  //   SignUp
  // }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
body{
  padding: 0;
  margin:0;
}
.logo{
        width: 100px;
    }

    .register input, .login input, .add input, .update input {
        width: 300px;
        height: 40px;
        padding-left: 20px;
        display: block;
        margin-bottom: 30px;
        margin-left: auto;
        margin-right: auto;
        border: 1px solid skyblue;
    }

    .register button, .login button, .add button, .update button{
        width: 320px;
        height: 40px;
        border: 1px solid skyblue;
        background: skyblue;
        color: white;
        cursor: pointer;

    }
</style>
