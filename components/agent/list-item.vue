<script setup>
const props = defineProps({
    agent: Object,
})
</script>

<template>
    <v-card variant="tonal" class="pa-4" @click="navigateTo(`/agent/${agent.uuid}`)">
        <div class="d-flex flex-column align-center">
            <v-avatar size="96" :image="agent?.displayIcon"></v-avatar>
            <div class="font-weight-bold text-h6 mt-4">
                {{ agent.displayName }}
            </div>
            <div class="text-medium-emphasis">
                {{ agent?.role?.displayName }}
            </div>
        </div>
    </v-card>
</template>