<template>
  <form @submit="onSubmit($event)" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input v-model="text" type="text" name="tex" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input v-model="day" type="text" name="day" placeholder="Add Day & Time" />
    </div>
    <div class="form-control check">
      <label>Set Reminder</label>
      <input v-model="reminder" type="checkbox" name="reminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>

export default {
	name: 'AddTask',
  data() {
    return {
      text: '',
      day: '',
      reminder: false
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();

      if(!this.text) {
        alert('Please add a task');
        return;
      }

      const newTask = {
        id: Math.floor(Math.random() * 100000),
        text: this.text,
        day: this.day,
        reminder: this.reminder
      }

      this.$emit('add-task', newTask);

      this.text = '';
      this.day = '';
      this.reminder = false;
    }
  }
}
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0;
}

.form-control label {
  display: block;
}

.form-control input {
  width: 100%;
  height: 40px;
  font-size: 17px;
}

.check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.check label {
  flex: 1;
}

.check input {
  flex: 2;
  height: 20px;
}
</style>
  