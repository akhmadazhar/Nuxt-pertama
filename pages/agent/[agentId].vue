<script setup>
const { agentId } = useRoute().params

const { data: agent, pending } = useLazyFetch(`https://valorant-api.com/v1/agents/${agentId}`,
    {
        onResponse({ response }) {
            const data = response._data?.data
            const abilities = data?.abilities
            selectedAbility.value = abilities?.at?.(0)
        },
        server: false,
    }
)

const selectedAbility = ref()
function selectAbility(ability) {
    selectedAbility.value = ability
}

</script>

<template>
    <v-theme-provider theme="dark" with-background>
        <v-img src="/bg1.jpg" cover>
            <div>
                <v-btn variant="text" prepend-icon="mdi-arrow-left" @click="navigateTo('/agent')">
                    Agent List
                </v-btn>
            </div>
            <h1 class="text-center mt-10">Agent - {{ agent?.data.displayName }}</h1>

            <v-row v-if="agent?.data" class="pa-4">
                <v-col v-if="$vuetify.display.mdAndUp" md="4">
                    <v-img :src="agent.data.background" />
                </v-col>
                <v-col cols="12" md="4">
                    <div class="d-flex">
                        <v-img :src="agent.data.fullPortraitV2" height="700" cover />
                    </div>
                </v-col>
                <v-col class="px-4" md="4">
                    <div class="d-flex flex-column">
                        <div class="">{{ agent.data.role.displayName }}</div>
                        <div class="mb-8 text-h2 font-weight-bold text-uppercase">{{ agent.data.displayName }}</div>
                    </div>
                    <v-row>
                        <v-col cols="12">
                            <v-row>
                                <v-col cols=2>
                                    <v-card width="64" height="64" color="" class="pa-3">
                                        <v-img :src="agent.data.role.displayIcon" />
                                    </v-card>
                                </v-col>
                                <v-col>
                                    <v-card variant="tonal" class="pa-4">{{ agent.data.description }}</v-card>
                                </v-col>
                            </v-row>
                        </v-col>
                        <v-col v-for="ability in agent.data.abilities.filter(a => a.slot != 'Passive')" :key="ability.slot"
                            cols="3">
                            <v-card @click="selectAbility(ability)" class="pa-3 mb-3" color="">
                                <!-- <div class="text-center text-caption mb-3">{{ ability.slot }}</div> -->
                                <v-img :src="ability.displayIcon" />
                            </v-card>

                        </v-col>
                    </v-row>
                    <v-card variant="tonal" :title="selectedAbility?.displayName" :text="selectedAbility?.description"
                        class="mt-6">

                    </v-card>
                </v-col>
            </v-row>

        </v-img>
    </v-theme-provider>
</template>
