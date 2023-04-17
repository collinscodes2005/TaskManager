<template>

  <div class="container">

    <AppHeader title="Task Tracker" />
    <div>
        <AddTask v-if="showAddTask" @add-task="addTask"  />
    </div>

    <TaskList @toogle-reminder="toogleReminder" @delete-task="deleteTask" :tasks="tasks" />

</div>
</template>


<script> 

//import AppHeader from AppHeader 
import AppHeader from './components/AppHeader'
import TaskList from './components/Tasks'
import AddTask from './components/AddTask'

//exporting defaults 
export default {
  name: 'App',
  components: {
    AppHeader,
    TaskList,
    AddTask,

  },

  data() {
    return { 
      tasks : [],
      showAddTask : false,
    }
  },
  methods : {

    //defining methods in my app :
    deleteTask(id){
        this.tasks = this.tasks.filter((task) => task.id !== id)
       console.log(id)
    },

    //method to toggle the reminder : 
    toogleReminder(id){
      this.tasks = this.tasks.map((task) => 
        task.id === id ? {...task, reminder: !task.reminder} : task)

    },
 
    //function to add a new task 
    addTask(task){
      this.tasks = [...this.tasks, task]

    }
  },

  created(){
    this.tasks = [
      {
        id : 1,
        text : "Doctos appointment",
        day : "March 1st at 2pm",
        reminder : true,
      },
      {
        id : 2,
        text : "Lecturers appointment",
        day : "March 1st at 2pm",
        reminder : true,
      },
      {
        id : 3,
        text : "Bank appointment",
        day : "March 1st at 2pm",
        reminder : true,
      },
    ]

  }
}


</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  width: 90%;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
