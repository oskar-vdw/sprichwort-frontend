<script setup lang="ts">
import SprichwortComponent from './SprichwortComponent.vue';

const dummyArrayList = [
    {
        "sprichwort": "Aller Anfang ist schwer.",
        "erklaerung": "Etwas Neues zu beginnen, ist schwierig.",
        "icon": "start"
    },
    {
        "sprichwort": "Alles hat ein Ende, nur die Wurst hat zwei.",
        "erklaerung": "Alles ist endlich.",
        "icon": "theaters"
    },
    {
        "sprichwort": "Alles hat seine Zeit.",
        "erklaerung": "Man soll nichts \u00fcberst\u00fcrzen.",
        "icon": "hourglass_empty"
    },
    {
        "sprichwort": "Allzu viel ist ungesund.",
        "erklaerung": "\u00dcbertreibung ist schlecht.",
        "icon": "warning"
    }
]


</script>

<template>
    <div class="greetings">
        <h3>
            Welches Sprichwort ist cooler?
        </h3>
    </div>
    <div class="sprichwort-container">
        <SprichwortComponent v-for="(itemDumy, index) in dummyArrayList" :key="index" :content=itemDumy.sprichwort
            :explanation=itemDumy.erklaerung :icon=itemDumy.icon />
    </div>
</template>

<style scoped></style>
