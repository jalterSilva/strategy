<template>
    <Navbar :logo="logo_src" :alt="app_name"/>
      <router-view/> <!-- parecido com render body -->
    <Footer :date="dateTime"/>

</template>

<script>
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'

export default{
  components:{
    Navbar,
    Footer
  },
  data(){
    return{
      logo_src: "/img/logo.svg",
      app_name: "Strategy",
      dateTime: new Date().getFullYear(),
    }
    
  }
}

</script>

<style>
*{
  font-family: Helvetica;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
   
}

h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}

a{
  text-decoration: none;
   color: #808080;
   font-weight: bold;
  transition: .3s;
}

a:hover{
  color: #666666;

}
</style>

