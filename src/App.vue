<template>
  <TheHeader title="Learning Resource"></TheHeader>
  <TheResources></TheResources>
</template>

<script>
import TheHeader from './components/layout/TheHeader.vue';
import TheResources from './components/TheResources.vue';

export default {
  components: { 
    TheResources,
    TheHeader 
  },
  
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>