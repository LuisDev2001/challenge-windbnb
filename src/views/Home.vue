<template>
  <div class="home wrapper">
    <section class="home__header">
      <h2>Stays in Finland</h2>
      <span>12+ stays</span>
    </section>

    <section class="grid">
      <!-- Component Card for Home -->
      <PxCard
        v-for="infoHome in data"
        :key="infoHome.id"
        :url="infoHome.url"
        :host="infoHome.host"
        :house="infoHome.houseInfo"
        :starsPoints="infoHome.starsPoints"
        :description="infoHome.description"
      />
    </section>

    <!-- Component Create by -->
    <PxCreate />
  </div>
</template>

<script>
// @ is an alias to /src
import PxCard from "@/components/Card/PxCard";
import PxCreate from "@/components/PxCreate";

import { reactive, toRefs } from "vue";
export default {
  name: "Home",
  setup() {
    const infoHome = reactive({
      data: [
        {
          id: 1,
          url: "../assets/img/imagen1.png",
          host: true,
          houseInfo: "Entire apartment . 2 beds",
          starsPoints: "4.40",
          description: "Stylist apartment in center of the city",
        },
        {
          id: 2,
          url: "../assets/img/imagen2.png",
          host: false,
          houseInfo: "Private room",
          starsPoints: "4.25",
          description: "Cozy, peaceful and private room with...",
        },
        {
          id: 3,
          url: "../assets/img/imagen3.png",
          host: false,
          houseInfo: "Entire house",
          starsPoints: "4.96",
          description: "Mordern House in a remote area",
        },
        {
          id: 4,
          url: "../assets/img/imagen4.png",
          host: true,
          houseInfo: "Entire apartment . 2 beds",
          starsPoints: "4.85",
          description: "Stylist room in design district",
        },
        {
          id: 5,
          url: "../assets/img/imagen5.png",
          host: false,
          houseInfo: "Private room",
          starsPoints: "4.54",
          description: "Modern apartment close to nature",
        },
        {
          id: 6,
          url: "../assets/img/imagen6.png",
          host: false,
          houseInfo: "Entire house",
          starsPoints: "4.64",
          description: "House in a remote area",
        },
      ],
    });

    return {
      ...toRefs(infoHome),
    };
  },
  components: {
    PxCard,
    PxCreate,
  },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/sass/views/_home.scss";
</style>
