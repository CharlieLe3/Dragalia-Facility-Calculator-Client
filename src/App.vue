<template>
  <div id="app">
    <Navbar></Navbar>
    <FireAltar></FireAltar>
  </div>
  
</template>

<script>
import Navbar from './components/Navbar';
import Home from './components/Home';
import FireAltar from './components/FireAltar';

export default {
  name: 'App',
  components: {
    Navbar,
    Home,
    FireAltar
  }
}


</script>

<style>
</style>
