<template>
    <v-container fluid>
        <v-row dense>
            <v-col
                v-for="card in 10"
                :key="card"
            >
                <v-card
                    class="mx-auto"
                    max-width="344"
                    elevation="4"
                    outlined
                >
                    <v-card-title>To Do List 1</v-card-title>
                    <v-card-text>Go to Bank, shopping, gym, lunch, drink, movie theater, book store and home</v-card-text>
                    <v-card-action>
                        <v-icon
                            class="ml-2 mb-2"
                            color="blue"
                        >
                            mdi-delete
                        </v-icon>
                    </v-card-action>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
    name: 'ToDoCard.vue',
    data() {
        return {
            toDoList: [],
            task: "",
        };
    },
});
</script>

<style scoped>
</style>
