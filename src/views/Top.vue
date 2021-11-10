<template>
  <v-form>
    <v-container>
      <v-dialog v-model="dialog" width="500">
        <template v-slot:activator="{ on, attrs }">
          <v-text-field v-model="card.task" placeholder="write a task">
            <v-icon
              v-if="!taskIsEmpty"
              @click="addTask"
              slot="append"
              color="blue"
              v-bind="attrs"
            >
              mdi-plus
            </v-icon>
            <v-icon v-else slot="append" color="blue" v-bind="attrs" v-on="on">
              mdi-plus
            </v-icon>
          </v-text-field>
          <h2 v-if="completeTodo">Completed All To Do Lists!</h2>
          <ToDoCard :todo="toDoList" />
        </template>

        <v-card>
          <v-card-text>
            <div class="d-flex justify-center pt-13 text-h5">
              Please write your task.
            </div>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="primary" text @click="dialog = false"> OK </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
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
      dialog: false,
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
    taskIsEmpty(): boolean {
      return this.card.task === "";
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
