<template>
    <div :key="task.id" v-for="task in tasks">
        
        <singleTask @toogle-reminder="$emit('toogle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)" :task="task" />

    </div>
</template>

<script>
import singleTask from './Task.vue'

export default {
    name : 'TaskList',
    props : {
       tasks : Array
    },

    components: {
        singleTask
    },
    
    emits : ['delete-task', 'toogle-reminder']

    
}

</script>
