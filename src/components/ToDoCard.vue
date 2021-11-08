<template>
    <v-container fluid>
        <v-row dense>
            <v-col
                v-for="card in todo"
                :key="card"
            >
                <v-card
                    class="mx-auto"
                    max-width="344"
                    elevation="4"
                    outlined
                >
                    <v-card-title>To Do List {{ card.count }}</v-card-title>
                    <v-card-text>{{ card.task }}</v-card-text>
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
    name: 'ToDoCard',
    data() {
        return {
            toDoList: [],
        };
    },

    props: {
        todo: {
            type: Array,
        }
    },

    computed: {
    }
});
</script>

<style scoped>
</style>
