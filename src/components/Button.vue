<template>
    <button :style="style">{{ text }}</button>
</template>

<script setup>
defineProps({
    text:{
        type: String,
        default: 'Add',
    },
    style:{
        type: String,
        default: ''
    }
})
</script>

<style>
button{
    all: unset;
    background-color: var(--color-background);
    cursor: pointer;
    border: solid 2px gray;
    padding: 3px 7px;
    border-radius: 15px;
    transition: all 250ms ease;
}
button:hover{
    scale: 1.1;
}
</style>