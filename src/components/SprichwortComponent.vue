<script setup lang="ts">

const props = defineProps<{
    content: string,
    explanation: string,
    icon: string
}>()
</script>

<template>
    <div class="sprichwort-container">
        <p class="sprichwort">„</p>
        <p class="sprichwort"> {{ props.content }}</p>
        <p class="erklaerung"> {{ props.explanation }}</p>
        <i class="material-icons">{{ icon }}</i>
    </div>
</template>

<style scoped>
.sprichwort {
    font-weight: bold;
    font-family: 'Georgia', Times, serif;
    font-size: 1.25em;
    /* color: var(--vt-c-text-dark-1) */

}

.erklaerung {
    font-family: 'Georgia', Times, serif;
    font-style: italic;
    /* color: var(--vt-c-text-dark-2) */
}

.sprichwort-container {
    /* background-color: var(--vt-c-text-dark-1); */
    margin: 1em 0 1em 0;
    outline: 1px var(--color-text) solid;
    outline-offset: -0.5em;
    border-radius: 1em;
    display: flex;
    padding: 2em;
    flex-direction: column;
    align-items: left;
    justify-content: center;
}
</style>
