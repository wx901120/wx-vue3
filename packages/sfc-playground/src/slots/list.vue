<script setup lang="ts" >
import { defineProps, ref } from 'vue';

const props = defineProps(['api-url','per-page'])
const items = ref([])

// mock data
setTimeout(() => {
    items.value = [
        { body: 'Scoped Slots Guide', username: 'Evan You', likes: 20 },
        { body: 'Vue Tutorial', username: 'Natalia Tepluhina', likes: 10 }
    ]
}, 3000);
</script>
<template>
    <ul>
        <li v-if="!items.length">
            Loading...
        </li>
        <li v-for="item of items">
            <!-- 通过 v-bind -->
            <slot name="item" v-bind="item"></slot>
        </li>
    </ul>
</template>
<style scoped>
ul{
    list-style-type: none;
    padding: 5px;
    background: linear-gradient(315deg, #42d392 25%, #647eff);
}
li{
    padding: 5px 20px;
    margin: 10px;
    background: #fff;
}
</style>