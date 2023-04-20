<template>
  <TheHeader title="Learning Resource"></TheHeader>
  <ResourceList :resources="storedResources"></ResourceList>
</template>

<script>
import TheHeader from './components/layout/TheHeader.vue';
import ResourceList from './components/ResourceList.vue';

export default {
  components: { 
    ResourceList,
    TheHeader 
  },
  data() {
    return {
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official guide',
          description: 'This is Vue official guide.',
          url: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'You can search anything on Google.',
          url: 'https://google.com'
        }
      ]
    }
  }
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