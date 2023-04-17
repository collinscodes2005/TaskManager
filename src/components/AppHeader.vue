<template>
    <header>
        <h1> {{title}} </h1>
    </header>

    <newButton text="Add Task" color="blue" /> 
    <newButton text="Delete Task" color="red" />

   

</template>

<script>

import newButton from './Button'

export default {
    name: 'AppHeader', 
    props: ['title'],
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