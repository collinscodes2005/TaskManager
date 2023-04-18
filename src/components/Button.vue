<template>
    <button @click="onClick" :style="{background: color}" class="btn">{{ text }}</button>
</template>
<script>
export default {
    name : 'newButton',
    props: ['text', 'color'],

    methods : {
        onClick() {
            this.$emit('btn-click')     
        }
    }
}
</script>