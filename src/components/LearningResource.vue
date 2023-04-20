<template>
  <li>
    <header>
      <h3>{{ title }}</h3>
      <button type="button">Delete</button>
    </header>
    <div>
      <p>{{ description }}</p>
      <a :href="url">Go website</a>
    </div>
  </li>
</template>

<script>
export default {
  props: ['title', 'description', 'url'],
  data() {

  }
} 
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>