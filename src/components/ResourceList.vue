<template>
  <ul>
    <LearningResource 
      v-for="resource in resources" 
      :key="resource.id" 
      :title="resource.title" 
      :description="resource.description" 
      :url="resource.url">
    </LearningResource>
  </ul>
</template>

<script>
import LearningResource from './LearningResource.vue';

export default {
  components: { LearningResource },
  inject: ['resources']
}
</script>

<style>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>