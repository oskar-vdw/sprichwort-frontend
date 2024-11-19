<script setup lang="ts">
import axios from 'axios';
import { onMounted, ref } from 'vue';
import SprichwortComponent from '../components/SprichwortComponent.vue';


onMounted(() => {
    getMatch();
});

const error = ref()

const sprichwortMatch = ref()

const getMatch = async () => {
    try {
        const response = await axios.get(`${import.meta.env.VITE_APP_BASEURL}/match`);
        sprichwortMatch.value = response.data; // Assign the API response
    } catch (err) {
        error.value = (err as Error).message; // Handle the error
        console.error('API Error:', err);
    }
}


</script>

<template>
    <div class="greetings">
        <h3>
            Welches Sprichwort ist cooler?
        </h3>
    </div>

    <div class="vote-container">
        <SprichwortComponent v-for="(item, index) in sprichwortMatch" :key="index" :content="item.content"
            :explanation="item.explanation" :icon="item.icon" />
    </div>
</template>

<style scoped></style>
