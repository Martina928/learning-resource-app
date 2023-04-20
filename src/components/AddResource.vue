<template>
  <BaseCard>
    <form @submit.prevent="onSubmit()">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" name="title" id="title" v-model.trim="title">
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea name="description" id="description" cols="30" rows="10" v-model="description"></textarea>
      </div>
      <div class="form-control">
        <label for="url">Link</label>
        <input type="url" name="url" id="url" v-model.trim="url">
      </div>
      <div class="btn-wrapper">
        <BaseButton type="submit">Submit</BaseButton>
      </div>
    </form>
  </BaseCard>
</template>

<script>
export default {
  emits: ['addResource'],
  data() {
    return {
      title: "",
      description: "",
      url: ""
    };
  },
  methods: {
    onSubmit() {
      this.$emit('addResource', this.title, this.description, this.url)
      this.title = '';
      this.description = '';
      this.url = '';
    }
  }
}
</script>

<style>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}

.btn-wrapper {
  text-align: end;
}
</style>