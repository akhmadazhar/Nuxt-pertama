<script setup>
const props = defineProps({
    icon: String,
    title: String,
    text: String,
})
</script>

<template>
    <v-card>
        <div class="d-flex flex-column align-center">
            <v-icon :icon="icon" size="128" />
            <v-card-title>{{ title }}</v-card-title>
            <v-card-text>{{ text }}</v-card-text>
        </div>
    </v-card>
</template>