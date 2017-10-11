<template>
  <img class="adminlogo" @click="gotoLogin" style="cursor:pointer" src="/static/AdminLogin.png">
</template>

<script>
  import VueRouter from 'vue-router';

  // code below executes a function that shoots the user over to the admin login page 
  export default {
    methods: {
        gotoLogin:function() {
        	this.$router.push('login')
        }
    }
}

</script>

<style>
.adminlogo {
  width: 10%;
  height: 100%;
  display: inline;
  float: right;
}
</style>