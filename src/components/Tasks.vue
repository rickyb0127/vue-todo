<template>
  <div v-for="task in tasks" :key="task.id">
    <Task @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="onDelete(task.id)" :task="task"></Task>
  </div>
</template>

<script>

import Task from './Task.vue';

export default {
	name: 'Tasks',
  components: {
    Task
  },
	props: {
		tasks: Array
	},
  methods: {
    onDelete(id) {
      console.log(id)
      this.$emit('delete-task', id);
    }
  },
  emits: ['toggle-reminder']
}
</script>

<style>
</style>
  