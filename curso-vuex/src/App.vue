<template>
  <div id="app">

      <router-link to="/">Home</router-link>
      <router-link to="/tasks">Lista de tarefas({{totalTasksNotCompleted }})</router-link>


      <router-view></router-view>
  </div>
</template>

<script>
export default {
    name: 'app',
    data() {
      return {

      }
    },
    computed: {
      totalTasksNotCompleted() {
        return this.$store.getters.tasksNotCompleted.length
      }
    }
}
</script>

<style>

</style>
