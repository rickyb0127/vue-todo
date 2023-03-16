<template>
  <div class="container">
    <Header @toggle-add-task-form="toggleAddTaskForm" :showAddTask="showAddTask" title="Task Tracker"></Header>
    <AddTask v-if="showAddTask" @add-task="addTask"></AddTask>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"></Tasks>
  </div>
</template>

<script>

import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data() {
		return {
			tasks: [],
      showAddTask: false
		}
	},
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id);
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => {
        const newReminder = task.id === id ? !task.reminder : task.reminder;

        return {
          ...task,
          reminder: newReminder
        }
      });
    },
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask];
    },
    toggleAddTaskForm() {
      this.showAddTask = !this.showAddTask;
    }
  },
	async created() {
		this.tasks = [
			{
				id: 1,
				text: "Doctor's Appointment",
				day: "March 1st at 2:30PM",
				reminder: true
			},
			{
				id: 2,
				text: "Meeting at School",
				day: "March 3rd at 2=1:30PM",
				reminder: true
			},
			{
				id: 3,
				text: "Food Shopping",
				day: "March 3rd at 11:00AM",
				reminder: false
			}
		]
	}
}
</script>

<style>
.container {
  margin-left: 10px;
  margin-right: 10px;
  padding-left: 20px;
  padding-right: 20px;
  border: 1px black solid;
}
</style>
