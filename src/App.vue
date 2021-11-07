<template>
  <v-app>
    <v-main>
      <Top />
      <ToDoCard />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from "vue";
import Top from "./views/Top.vue";
import ToDoCard from "./components/ToDoCard.vue";

export default Vue.extend({
  name: "App",

  components: {
    Top,
    ToDoCard,
  },

  data: () => ({
    //
  }),
});
</script>
