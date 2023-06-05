<template>
  <div class="card p-3 mb-3" :class="{ completed: task.completed }">
    <div class="d-flex">
      <input type="checkbox" v-model="isDone" @change="toggleCompleted" />
      <h3>{{ task.title }}</h3>
    </div>
    <p class="text-lg">{{ task.description }}</p>
    <button
      class="btn btn-primary"
      @click="
        {
          showModal = !showModal;
        }
      "
    >
      more
    </button>
    <button class="btn btn-danger" @click="deleteTask">&#x2715;</button>
    <MoreModal v-show="showModal" @close-modal="closeModal">{{
      task.description
    }}</MoreModal>
  </div>
</template>
<script>
import MoreModal from "@/components/MoreModal.vue";

export default {
  data() {
    return {
      isDone: this.task.completed,
      showModal: false,
    };
  },
  props: {
    task: {
      type: Object,
    },
  },
  methods: {
    deleteTask() {
      this.$emit("delete-task", this.task.id);
    },
    toggleCompleted() {
      this.$emit("toggle-completed", this.task.id);
    },
    closeModal() {
      this.showModal = false;
    },
  },
  components: { MoreModal },
};
</script>
<style>
.completed {
  background: lightgreen;
}
.card {
  position: relative;
}
.card input {
  margin-right: 20px;
}
.btn-danger {
  position: absolute;
  top: 20px;
  right: 20px;
  color: #fff;
}
.text-lg {
  height: 24px;
  overflow: hidden;
}
.btn-primary {
  max-width: 100px;
  margin: auto;
}
</style>
