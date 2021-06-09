<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">Shuffle and Sort</div>
    </v-app-bar>

    <v-main>
      <shuffle-sort></shuffle-sort>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import ShuffleSort from './components/ShuffleSort.vue';

@Component({
  components: {
    ShuffleSort,
  },
})
export default class App extends Vue {}
</script>
<style>
html {
  overflow-y: auto !important;
}
</style>
