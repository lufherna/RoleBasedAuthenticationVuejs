<template>
<section class="header row">
<div class="col-lg-6 col-md-6">
  <h1 v-on:click="home()" style="cursor:pointer;">Reclaim Romance</h1>
</div>
<Admin></Admin>
<div class="col-lg-6 col-md-6">
    <h2 v-on:click="logout()" style="cursor:pointer;" v-if="checkLogin">Logout</h2>
</div>
</section>
</template>

<script>
  import VueRouter from 'vue-router';
  // code below pulls the pictures located in a different area
  import Admin from './AdminLogo'
  
  export default {
    components: {
    Admin
    },
    data() {
      return {
        message:'Header'
      }
    },
    methods: {
        logout:function() {
           var app = this;
         localStorage.removeItem("lbUser");
         app.$router.push({ name: 'login'});
         app.$store.state.isLoggedIn = false;
        },
        home:function() {
          this.$router.push('/')
        }
    },
    computed: {
      checkLogin() {
        return this.$store.state.isLoggedIn;
      }
    }
  }

</script>

<style>
</style>