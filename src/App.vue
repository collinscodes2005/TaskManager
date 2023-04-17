<template>

  <div class="container">

    <AppHeader title="Task Tracker" />

    <TaskList :tasks="tasks" />

</div>
</template>

<script>

//import AppHeader from AppHeader 
import AppHeader from './components/AppHeader'
import TaskList from './components/Tasks'

//exporting defaults 
export default {
  name: 'App',
  components: {
    AppHeader,
    TaskList,

  },

  data() {
    return { 
      tasks : []
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
  max-width: 500px;
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
