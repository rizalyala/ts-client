<template>
  <img src="./assets/logo.svg" alt="">
  <HalamanAwal msg="daftar mahasiswa"/>
</template>

<script>
  import HalamanAwal from './components/HalamanAwal.vue';
  export default{
    name:'App',
    components:{
      HalamanAwal
    }
  }
</script>

<style>
  #app{
    font-family: Arial, Helvetica, sans-serif;
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>