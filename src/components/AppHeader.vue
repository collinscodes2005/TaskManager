<template>


    <header>
        <h1> {{title}} </h1>
   

         <newButton  @btn-click="$emit('toogle-add-task')" :text="showAddTask ? 'Close' :  'Add Task' " :color="showAddTask ? 'red' : 'green' " /> 
    <!-- <newButton text="Delete Task" color="red" /> -->

    </header>

</template>

<script> 

import newButton from './Button'

export default {
    name: 'AppHeader', 
    props: {
        title : String,
        showAddTask : Boolean

    },
    components:{ 
        newButton
    },
}
</script>

<style scoped>

header{
    display: flex;
    justify-content: space-around;
    align-items: center;
    margin-bottom: 20px;
}

</style>