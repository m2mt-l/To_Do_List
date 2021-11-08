<template>
  <v-form v-model="valid">
    <v-container>
      <v-text-field
        v-model="card.task"
        :rules="rules"
        placeholder="write a task"
      >
        <v-icon
          @click="addTask"
          slot="append"
          color="blue"
        >
        mdi-plus
        </v-icon>
      </v-text-field>
      <ToDoCard :todo="toDoList"/>
    </v-container>

  </v-form>
</template>

<script lang="ts">
import Vue from 'vue';
import ToDoCard from "../components/ToDoCard.vue";

export default Vue.extend({
    name: 'Top',

    components: {
      ToDoCard,
    },
    
    data() {
        return {

          toDoList: [],
          card:{
            task: "",
            count: 0,
          },
        };
    },


    methods: {
      addTask(): void {
        this.card.count++;
        this.toDoList.push(this.card);
      },
    },

    computed: {
/*
      writeTask: {
        set(value: string) {
          this.card.task = value;
        }
      }
*/
    }

});
</script>

<style scoped>
</style>
