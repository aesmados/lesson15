<template>
  <div class="container">
    <h1>Task App</h1>
    <TaskList />
  </div>
</template>

<script>
import TaskList from "@/components/TaskList.vue";
export default {
  components: { TaskList },
};
</script>
