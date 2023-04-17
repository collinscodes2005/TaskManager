<template>
    <button :style="{background: color}" class="btn">{{ text }}</button>
</template>
<script>
export default {
    name : 'newButton',
    props: ['text', 'color'],
}
</script>