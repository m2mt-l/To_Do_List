<template>
  <v-form v-model="valid">
    <v-container>
      <v-text-field
        v-model="toDoList"
        :rules="rules"
        placeholder="write a task"
      >
        <v-icon
          slot="append"
          color="blue"
        >
        mdi-plus
        </v-icon>
      </v-text-field>
    </v-container>
  </v-form>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
    name: 'Top',
    data() {
        return {
            Card:{
              task: "",
            }
        };
    },
});
</script>

<style scoped>
</style>
