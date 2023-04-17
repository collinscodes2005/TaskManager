<template>
    <button  :style="{background: color}" class="btn">{{ text }}</button>
</template>
<script>
export default {
    name : 'newButton',
    props: ['text', 'color'],

    methods : {
        onclick() {
            this.$emit('toogle-add-task')     
        }
    }
}
</script>