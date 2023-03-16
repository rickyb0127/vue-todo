<template>
	<button class="btn" @click="this.$emit('toggle-add-task-form')" :style="{backgroundColor: color}">{{ text }}</button>
</template>

<script>

export default {
	name: 'Button',
	props: {
		text: String,
		color: String
	}
}
</script>

<style scoped>
.btn {
	border-radius: 3px;
	cursor: pointer;
	color: white;
	height: 32px;
}
</style>