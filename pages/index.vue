<script setup>

</script>

<template>
    <v-container class="fill-height">
        <v-row>
            <v-col>
                <menu-card icon="mdi-clipboard-check" title="Todo List" text="Berisi Contoh Todo List"
                    @click="navigateTo('/todo')" />
            </v-col>

            <v-col>
                <menu-card icon="mdi-crosshairs-gps" title="Valorant API" text="Berisi penggunaan API Valorant"
                    @click="navigateTo('/agent')" />
            </v-col>
        </v-row>

    </v-container>
</template>