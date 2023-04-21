<template>
  <BaseDialog v-if="isInvalid" @close="confirmError">
    <template #default>
      <p>Unfortunately, at least one input value is invalid.</p>
      <p>Please check all inputs and make sure you enter at least a few characters.</p>
    </template>
    <template #action>
      <BaseButton @click="confirmError"></BaseButton>
    </template>
  </BaseDialog>

  <BaseCard>
    <form @submit.prevent="onSubmit">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" name="title" id="title" ref="title">
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea name="description" id="description" cols="30" rows="10" ref="description"></textarea>
      </div>
      <div class="form-control">
        <label for="url">Link</label>
        <input type="url" name="url" id="url" ref="url">
      </div>
      <div class="btn-wrapper">
        <BaseButton type="submit">Submit</BaseButton>
      </div>
    </form>
  </BaseCard>
</template>

<script>
export default {
  inject: ["addResource"],
  data() {
    return {
      isInvalid: false,
    };
  },
  methods: {
    onSubmit() {
      let title = this.$refs.title.value;
      let description = this.$refs.description.value;
      let url = this.$refs.url.value;

      if (title.trim() === "" || description.trim() === "" || url.trim() === "") {
        console.log(this.isInvalid)
        this.isInvalid = true;
        return;
      }
      this.$emit("addResource", title, description, url);
    },
    confirmError() {
      this.isInvalid = false;
    }
  },
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