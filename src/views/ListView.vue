<script setup lang="ts">
import axios from 'axios';
import { onMounted, ref } from 'vue';
import SprichwortComponent from '../components/SprichwortComponent.vue';


onMounted(() => {
    getList();
});

const sprichwortList = ref()

const data = ref()
const error = ref()

const getList = async () => {
    try {
        const response = await axios.get(`${import.meta.env.VITE_APP_BASEURL}/list`);
        sprichwortList.value = response.data; // Assign the API response
    } catch (err) {
        error.value = (err as Error).message; // Handle the error
        console.error('API Error:', err);
    }
}



const fetchData = async () => {
    try {
        const response = await axios.get(`${import.meta.env.VITE_APP_BASEURL}/hello`);
        data.value = response.data; // Assign the API response
    } catch (err) {
        error.value = (err as Error).message; // Handle the error
        console.error('API Error:', err);
    }
};
// import SprichwortComponent from '@/components/SprichwortComponent.vue';
</script>

<template>
    <h3>Die geordnete Liste aller Sprichwörter</h3>
    <button @click="fetchData"> Fetch</button>
    <p>{{ data }}</p>
    <p v-if="error">{{ error }}</p>
    <div class="sprichwort-container">
        <SprichwortComponent v-for="(sprichwort, index) in sprichwortList" :key="index" :content=sprichwort.content
            :explanation=sprichwort.explanation :icon=sprichwort.icon />
    </div>
</template>
