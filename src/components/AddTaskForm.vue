<template>
  <div>
    <div class="form1">
      <label >Task
        <input type="text" v-model.trim="newTask.title" @keyup.enter="addTask" size="41">
      </label>

      <select  v-model="newTask.priority">
        <option value="high">High</option>
        <option value="medium">Medium</option>
        <option value="low">Low</option>
      </select>

      <select  v-model="newTask.category">
        <option value="school">School</option>
        <option value="work">Work</option>
        <option value="home">Home</option>
        <option value="other">Other</option>
      </select>
</div>
      <br>

    <div class="form2">
      <label >Description
        <input type="text" v-model.trim="newTask.description" size="55">
      </label>
</div>
      <br>

    <div class="dd form3">
      <label >Due date
        <input type="date" v-model="newTask.dueDate">
      </label>
</div>
    <br>

    <div class="centerButton">
      <button class="addTask" @click="addTask">Add Task</button>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      newTask: {}
    }
  },

  created () {
    this.newTask = this.getNewTask()
  },

  methods: {
    addTask () {
      // this.taskList.push(this.newTask)
      this.$emit('taskAdded', this.newTask)
      this.newTask = this.getNewTask()
    },

    getNewTask () {
      const now = new Date()
      const today = now.toISOString().substr(0, now.toISOString().indexOf('T'))
      console.log(now)
      return {
        id: null,
        category: '',
        dueDate: today,
        isComplete: false,
        priority: 'medium',
        description: '',
        title: ''
      }
    }
  }
}
</script>

<style>

.addTask {
  background-color: #cc6600;
  border-style: none;
  height: 35px;
  width: 300px;
  margin-top: 20px;
  text-align: center;
  font-size: 16px;
  color: #f9f9f9;
  border-radius: 8px;
  margin-top: 0px;

}

.centerButton {
  text-align: center;
}

.dd {
  display: flex;
  justify-content: center;
}

.form1 {
  margin-top: 14px;
}

.form2 {
  margin-top: -10px;
}

.form3 {
  margin-top: -10px;

}





</style>
