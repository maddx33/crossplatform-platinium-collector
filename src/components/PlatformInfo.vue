<template>
  <div class="platform-info" ref="platform">
    <div style="text-decoration: underline">{{ platform }}</div>
    <div>Games: {{ games.length }}</div>
    <div>Completed: {{ fullCompleted }}</div>
    <div>Time spent: {{ timeSpent }}</div>
  </div>
</template>

<script lang="ts">
import { PlatiniumTrophy } from "@/types/types";
import PlatiniumCard from "@/components/PlatiniumCard.vue";
import { defineComponent, PropType } from "vue";
import "vue3-carousel/dist/carousel.css";
import { Carousel, Slide } from "vue3-carousel";
import { useRoute } from "vue-router";

export default defineComponent({
  props: {
    platform: String,
    games: {
      type: Object as PropType<PlatiniumTrophy[]>,
      required: true,
    },
  },
  computed: {
    fullCompleted() {
      return this.games.filter((i) => i.completionPercentage === 100).length;
    },
    timeSpent() {
      let sum = 0;
      this.games.forEach((p) => {
        sum += +p.timePlayed;
      });
      return sum;
    },
  },
});
</script>
<style lang="scss" scoped>
.platform-info div {
  z-index: 20;
  color: white;
  font-size: 2.5em;
  font-family: "Lato", sans-serif;
  -webkit-font-smoothing: antialiased;
}
</style>
