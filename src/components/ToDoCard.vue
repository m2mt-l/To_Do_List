<template>
    <v-container fluid>
        <v-row dense>
            <v-col v-for="(card, index) in todo" :key="card.count">
                <v-card
                    class="mx-auto"
                    max-width="500"
                    min-width="344"
                    elevation="4"
                    outlined
                >
                    <v-card-title>To Do List {{ card.count }}</v-card-title>
                    <v-card-text>{{ card.task }}</v-card-text>
                    <v-card-actions>
                        <v-icon
                            @click="deleteToDo(index)"
                            class="ml-2 mb-2"
                            color="blue"
                        >
                            mdi-delete
                        </v-icon>
                    </v-card-actions>
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
        },
    },

    methods: {
        deleteToDo(index: number) {
            this.$emit('delete');
            this.todo.splice(index - 1, 1);
        },
    },

    computed: {},
});
</script>

<style scoped></style>
