<template>
  <header class="header wrapper">
    <PxLogo />
    <PxSearch />
    <div class="overlay" ref="jsOverlay"></div>
  </header>
</template>

<script>
import PxSearch from "@/components/Header/PxSearch";
import PxLogo from "@/components/Header/PxLogo";

export default {
  name: "PxHeader",
  props: {},
  components: {
    PxSearch,
    PxLogo,
  },
};
</script>

<style scoped lang="scss">
@import "~@/assets/sass/components/Header/_PxHeader.scss";
</style>
