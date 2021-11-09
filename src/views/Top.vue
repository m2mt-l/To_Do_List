<template>
  <v-form>
    <v-container>
      <v-text-field v-model="card.task" placeholder="write a task">
        <v-icon @click="addTask" slot="append" color="blue"> mdi-plus </v-icon>
      </v-text-field>
      <h2 v-if="completeTodo">Completed All To Do Lists!</h2>
      <ToDoCard :todo="toDoList" />
    </v-container>
  </v-form>
</template>

<script lang="ts">
import Vue from "vue";
import ToDoCard from "../components/ToDoCard.vue";
import Card from "../card";

export default Vue.extend({
  name: "Top",

  components: {
    ToDoCard,
  },

  data() {
    return {
      toDoList: [] as Array<Card>,
      card: {
        task: "",
        count: 0,
      },
    };
  },

  methods: {
    addTask(): void {
      this.card.count++;
      let newCard: Card = new Card(this.card.task, this.card.count);
      this.toDoList.push(newCard);
      this.card.task = "";
    },
  },

  computed: {
    completeTodo(): boolean {
      return this.toDoList.length === 0 && this.card.count != 0;
    },
    /*
      writeTask: {
        set(value: string) {
          this.card.task = value;
        }
      }
*/
  },
});
</script>

<style scoped></style>
