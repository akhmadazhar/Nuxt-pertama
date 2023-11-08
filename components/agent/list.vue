<script setup>
const props = defineProps({
    agents: Array,
})
</script>

<template>
    <v-row>
        <v-col v-for="agent in agents || []" :key="agent.uuid" cols="12" sm="6" md="3">
            <agent-list-item :agent="agent" />
        </v-col>
    </v-row>
</template>