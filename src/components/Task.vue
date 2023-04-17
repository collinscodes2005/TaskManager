<template>

<div @dblclick="$emit('toogle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
<h3>{{task.text}}
  <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
 </h3>
<h4>{{task.day}}</h4>
</div>
</template>

<script>
export default {
    //name of component
    name : 'singleTask',
 
    //props 
    props : {
        task : Object
    },

    //methods 

}
</script>
<style>
.task{
    margin: 5px;
    background: rgba(244, 244, 244, 0.963);
    padding: 10px 20px;
    cursor: pointer;
}
.task h3{
    align-items: center;
    display: flex;
    justify-content: space-between;
}
.fas{
    color: red;
}
.task.reminder {
  border-left: 5px solid green;
}
</style>