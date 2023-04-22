<template>

  <div class="container">

    <AppHeader @toogle-add-task="toogleAddTask" title="Task Tracker" :showAddTask="showAddTask" />
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

  //my App components 
  components: {
    AppHeader,
    TaskList,
    AddTask,

  },

  //data for stateManagement
  data() {
    return { 
      tasks : [],
      showAddTask : false,
    }
  },
  methods : {

    //defining methods in my app :

    //method to delete a particular task 
    async deleteTask(id){
        const res = await fetch(`${this.apiUrl}/tasks/${id}/delete`,
        {
          method : 'DELETE',

        })

        res.status === 204 ? ( this.tasks = this.tasks.filter((task) => task.id !== id)) : 
        alert('Error deleting task')
       
       console.log(id)
    },

    //method to toggle the reminder : 
    async toogleReminder(id){
      const taskToUpdate = this.tasks.find(task => id === task.id);
      const updatedTask = {...taskToUpdate, reminder: !taskToUpdate.reminder};

      const res = await fetch(`${this.apiUrl}/tasks/${id}`, {
        method: 'PUT',
        headers: {
          'Content-type' : 'application/json'
        },
        body: JSON.stringify(updatedTask)

      })

      const data = await res.json()

      this.tasks = this.tasks.map(task => (task.id === id ? data : task))
      
       // task.id === id ? {...task, reminder: !task.reminder} : task)


    }, 
 
    //function to add a new task 
    async addTask(task){

      const res = await fetch(`${this.apiUrl}/tasks/`, {
        method: 'POST',
        headers : { 
          'Content-type' : 'application/json',
        },
          body : JSON.stringify(task),
             
      })

      const data = await res.json()

      this.tasks = [...this.tasks, data]
      //this.tasks = [...this.tasks, task]

    },

    //function to show new task form
    toogleAddTask() {
      this.showAddTask = !this.showAddTask
    },

    //function to fetch employees
    async fetchEmployees(){
      const res = await fetch(`${this.apiUrl}/tasks/`)
      const data =  await res.json()

      return data
    }
  }, 

  async created(){
    this.tasks = await this.fetchEmployees()

  },

  computed: {
  apiUrl() {
    return process.env.VUE_APP_API_URL;
  }
},
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