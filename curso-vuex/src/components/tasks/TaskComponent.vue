<template>
<div>
<h2>{{title}} </h2>
<TaskAddComponent />
      <ul>
        <li v-for="(task, index) in getTasksSorted" :key="index" :class="task.completed ? 'completed' : 'incompleto'">
            <a href="#" @click.prevent="completedTask(task)"> Clique para completar</a>
          {{task.name}}
        </li>
      </ul>
</div>
</template>

<script>
import TaskAddComponent from "./TaskAddComponent"

export default {

  components: {
    TaskAddComponent
  },
    data() {
        return {
            title: 'Lista de tarefas'
        }
    },

    methods: {
        completedTask(task) {
            this.$store.commit('TOOGLE_TASK', task)
        }
    },

    computed: {
        getTasks() {
            return this.$store.state.tasks
        },
        getTasksSorted() {
          return this.$store.getters.sortedTasks
        }
    }
}
</script>

<style scoped>
.completed{
  background: forestgreen;
}
.incompleto{
  background: red;
}
</style>
