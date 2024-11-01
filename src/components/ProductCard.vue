<template>
    <div class="flex-col card">
        <img :src="url" :alt="`${data.name} image`">
        <div class="flex-col">
            <p class="bold bigger">{{ data.name }}</p>
            <p>{{ data.category }}</p>
            <div class="flex-row space-between">
                <p class="big">${{ data.price }}</p>
                <p>{{ data.status }}</p>
            </div>
            <div class="flex-row space-between">
                <Button :text="'Edit'" @click="openAlert" />
                <Button :text="'Delete'" @click="$emit('delete')" :style="{'color':'red'}" />
            </div>
        </div>
    </div>
</template>

<script setup>
import { computed } from 'vue'
import Button from './Button.vue'

const props = defineProps({
    data: {
        type: Object,
        default: {
            "image":"NoImg",
            "name":"Default name",
            "price":"0",
            "category":"Default",
            "status":"Out of stock"
        },
    }
})

defineEmits(['delete'])

const openAlert = () => alert("Modal hasn't been implemented!")

const url = computed(() => {
     return new URL(`../assets/${props.data.image}.jpg`, import.meta.url).href
})
</script>

<style>
img{
    width:250px;
    height:250px;
    border-radius: 10px;
    border: solid 3px gray;
}
</style>