<template>
<v-container grid-list-md>
  <v-layout row wrap>
    <v-flex xs12>
         <router-link to="Signin"><img class="admin" src="/static/AdminLogin.png"></router-link><br>
    </v-flex>
  </v-layout>
    <div class="main">
      <div class="submain">
        <Logo></Logo>
        <Con></Con>
      </div>
    </div>
  </div>
  </v-container>
</template>

<script>
import Con from './ConMessage'
import Logo from './Logo'


export default {
  components: {
    Con,Logo
  },
  beforeCreate: function(){
  },
  name: 'Construction',
  data () {
    return {
  
    }
  }
}
</script>

<style scoped>
.admin{
  width: 10px;
  position: absolute;
  top: 0px;
  right: 0px;

}
.form{
    margin:0 auto;
  text-align: center;
  width: 75%;
  background-color: #f5f5f5;
}
.main{
  margin: 0px;

}
.submain{
  margin:0 auto;
  text-align: center;
  width: 100%;
  background-color: #f5f5f5;

}
.title{
  color:#424242; 
}
img{
  align: center;
  padding-top: 0px;
}
.content{
text-align: center;
height: 100%;

}
.over{
  color:#f7dfd4!important;
}
.message{
    color:#f7dfd4!important;
    font-weight: bold;
}
</style>