<template>
  <div class="row">
    <div class="col-lg-6">
      <TaskForm @add-task="addTask" />
    </div>
    <div class="col-lg-6">
      <p class="mb-3 mt-3">Total tasks: {{ totalTasks }}</p>
      <p class="mb-3 mt-3">Total done tasks: {{ totalDoneTasks }}</p>
      <TaskItem
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @delete-task="deleteTask"
        @toggle-completed="toggleCompleted"
      />
    </div>
  </div>
</template>
<script>
import TaskItem from "@/components/TaskItem.vue";
import TaskForm from "@/components/TaskForm.vue";
export default {
  components: { TaskItem, TaskForm },
  data() {
    return {
      tasks: [
        {
          id: 1,
          title: "title 1",
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Repellat, tenetur.",
          completed: false,
        },
        {
          id: 2,
          title: "title 2",
          description:
            "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Nesciunt neque iure deleniti temporibus laborum omnis veniam officiis quo dolorum unde.",
          completed: true,
        },
        {
          id: 3,
          title: "title 3",
          description:
            "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Ipsam illum amet aperiam qui dolores illo aspernatur provident labore, cumque totam! Facilis odit saepe aliquam laborum in doloribus incidunt dicta, quos nobis ipsum consequatur tempore itaque quo tempora libero veritatis, beatae illum ex hic quis earum? Pariatur nesciunt quisquam minus! Molestias. Lorem, ipsum dolor sit amet consectetur adipisicing elit. Ipsam illum amet aperiam qui dolores illo aspernatur provident labore, cumque totam! Facilis odit saepe aliquam laborum in doloribus incidunt dicta, quos nobis ipsum consequatur tempore itaque quo tempora libero veritatis, beatae illum ex hic quis earum? Pariatur nesciunt quisquam minus! Molestias.",
          completed: false,
        },
      ],
    };
  },
  computed: {
    totalTasks() {
      return this.tasks.length;
    },
    totalDoneTasks() {
      return this.tasks.filter((task) => task.completed).length;
    },
  },
  methods: {
    addTask(newTask) {
      this.tasks.push(newTask);
    },
    deleteTask(taskId) {
      this.tasks = this.tasks.filter((task) => task.id !== taskId);
    },
    toggleCompleted(taskId) {
      this.tasks = this.tasks.map((task) => {
        if (task.id === taskId) {
          task.completed = !task.completed;
        }
        return task;
      });
    },
  },
};
</script>
