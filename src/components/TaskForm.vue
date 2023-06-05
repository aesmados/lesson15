<template>
  <form @submit.prevent="submitForm">
    <h3>Create Task</h3>
    <input
      type="text"
      class="form-control mb-3"
      placeholder="Title"
      v-model="title"
    />
    <textarea
      name=""
      class="form-control mb-3"
      placeholder="Description"
      v-model="description"
    ></textarea>
    <button type="submit" class="btn btn-primary">Add task</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      description: "",
    };
  },
  methods: {
    submitForm() {
      const newTask = {
        id: Date.now(),
        title: this.title,
        description: this.description,
        completed: false,
      };
      this.$emit("add-task", newTask);
      this.title = "";
      this.description = "";
    },
  },
};
</script>
