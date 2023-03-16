<template>
	<header>
		<h1>{{ title }}</h1>
		<Button 
			@toggle-add-task-form="this.$emit('toggle-add-task-form')" 
			:text="showAddTask ? 'Close' : 'Add Task'" 
			:color="showAddTask ? 'red' : 'green'">
		</Button>
	</header>
</template>

<script>

import Button from './Button.vue';

export default {
	name: 'Header',
	components: {
    Button
  },
	props: {
		title: String,
		showAddTask: Boolean
	}
}
</script>

<style>
header {
	display: flex;
	justify-content: space-between;
	align-items: center;
	margin-bottom: 20px;
}
</style>
  