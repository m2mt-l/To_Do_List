<template>
    <v-form ref="form">
        <v-container>
            <v-text-field
                v-model="card.task"
                placeholder="write a task"
                :rules="nameRules"
                required
            >
                <v-icon @click="addTask" slot="append" color="blue">
                    mdi-plus
                </v-icon>
            </v-text-field>
            <h2 v-if="completeTodo">Completed All Tasks!</h2>
            <ToDoCard :todo="toDoList" @delete="validationReset" />
        </v-container>
    </v-form>
</template>

<script lang="ts">
import Vue from 'vue';
import ToDoCard from '../components/ToDoCard.vue';
import Card from '../models/card';

export default Vue.extend({
    name: 'Top',

    components: {
        ToDoCard,
    },

    data() {
        return {
            toDoList: [] as Array<Card>,
            card: {
                task: '',
                count: 0,
            },
            nameRules: [(v: any) => !!v || 'Task is required'],
        };
    },

    methods: {
        addTask(): void {
            if ((this.$refs as any).form.validate()) {
                this.card.count++;
                let newCard: Card = new Card(this.card.task, this.card.count);
                this.toDoList.push(newCard);
                this.validationReset();
            }
        },
        validationReset(): void {
            (this.$refs as any).form.reset();
        },
    },

    computed: {
        completeTodo(): boolean {
            return this.toDoList.length === 0 && this.card.count != 0;
        },
    },
});
</script>

<style scoped></style>
