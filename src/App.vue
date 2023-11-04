<template>
  <div class="components">
  <Navbar/>
  <RouterView />
  </div>
</template>

<script >
import { RouterLink, RouterView } from 'vue-router';
import Navbar from './components/Navbar.vue';
export default{
   components :{ Navbar},
};
</script>

<style>
body {
  background: #ffffc2;
  background-image: radial-gradient(#000 5%, transparent 0);
  background-size: 35px 35px;
}
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: absolute;
  top:0;
  right: 0;
  bottom:0;
  left: 0;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  margin: 0 auto;
  color: darkblue;
}
nav {
  padding: 20px;
  font-size: 20px;
}

nav a {
  font-weight: bold;
}
</style>
