<template>
    <div id="app">
      <LogUploader />
    </div>
  </template>
  
  <script>
  import LogUploader from './components/LogUploader.vue';
  
  export default {
    name: 'App',
    components: {
      LogUploader,
    },
  };
  </script>
  
  <style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    margin-top: 60px;
  }
 
  </style>
  