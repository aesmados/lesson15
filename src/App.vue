<template>
  <div class="container">
    <h1 class="mb-5 mt-5">Task App</h1>
    <TaskList />
  </div>
</template>

<script>
import TaskList from "@/components/TaskList.vue";
export default {
  components: { TaskList },
};
</script>
