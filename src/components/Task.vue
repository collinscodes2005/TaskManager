<template>

<div :class="[task.reminder ? 'reminder' : '', 'task']">
<h3>{{task.text}}
  <i @click="onDelete(task.id)" class="fas fa-times"></i>
 </h3>
<h4>{{task.day}}</h4>
</div>
</template>

<script>
export default {
    name : 'singleTask',
    props : {
        task : Object
    },

    methods : {
        onDelete(id){
            console.log(id)
        }
    }
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