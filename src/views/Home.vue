<template>
  <div class="home wrapper">
    <section class="home__header">
      <h2>Stays in Finland</h2>
      <span>12+ stays</span>
    </section>
    <section class="grid">
      <PxCard />
    </section>
  </div>
</template>

<script>
// @ is an alias to /src
import PxCard from "@/components/Card/PxCard";
export default {
  name: "Home",
  components: {
    PxCard,
  },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/sass/views/_home.scss";
</style>
