<template>
  <v-container>
    <v-row>
      <v-col sm="2" cols="12" order="1" order-sm="12" class="pa-3"
        ><v-btn
          class="ma-2"
          :class="$vuetify.breakpoint.xs ? 'min-width-btn' : 'min-width-btn-sm'"
          color="primary"
          @click="shuffle"
          >SHUFFLE</v-btn
        >
        <v-btn
          class="ma-2"
          :class="$vuetify.breakpoint.xs ? 'min-width-btn' : 'min-width-btn-sm'"
          color="primary"
          @click="sort"
          >SORT</v-btn
        >
      </v-col>
      <v-col sm="10" cols="12" order="12" order-sm="1" class="pa-3">
        <v-row no-gutters>
          <v-col cols="12" sm="4" v-for="item in items" :key="item.text">
            <v-card
              v-if="!$vuetify.breakpoint.xs"
              class="tac card-sm"
              :style="{ 'background-color': item.color }"
              ><h1 class="color-white">{{ item.text }}</h1></v-card
            >
            <v-card v-else class="tac card">
              <v-row no-gutters>
                <v-col cols="1" :style="{ 'background-color': item.color }">
                </v-col>
                <v-col cols="10"
                  ><h3 class="color-black">{{ item.text }}</h3></v-col
                >
              </v-row></v-card
            >
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>
<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class ShuffleSort extends Vue {
  private items = [
    { text: 1, color: '#2F454E' },
    { text: 2, color: '#2B8EAD' },
    { text: 3, color: '#6F98A8' },
    { text: 4, color: '#2B8EAD' },
    { text: 5, color: '#6F98A8' },
    { text: 6, color: '#818181' },
    { text: 7, color: '#818181' },
    { text: 8, color: '#2F454E' },
    { text: 9, color: '#6F98A8' },
  ];

  // Fisher-Yates algorithm
  shuffle(): void {
    for (let i = 0; i < this.items.length - 1; i += 1) {
      const j = i + Math.floor(Math.random() * (this.items.length - i));
      const origin = this.items[i];
      this.items[i] = this.items[j];
      Vue.set(this.items, j, origin);
    }
  }

  sort(): void {
    this.items.sort((a, b) => a.text - b.text);
  }
}
</script>
<style>
.min-width-btn {
  min-width: 33% !important;
}

.min-width-btn-sm {
  min-width: 100% !important;
}
.tac {
  text-align: center;
}
.card {
  min-height: 8vh;
  line-height: 8vh;
}
.card-sm {
  min-height: 25vh;
  line-height: 25vh;
}
.color-white {
  color: white;
}
.color-black {
  color: black;
}
</style>
