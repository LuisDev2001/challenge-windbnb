<template>
  <PxHeader />
  <router-view />
</template>

<script>
import PxHeader from "@/components/Header/PxHeader";

export default {
  components: {
    PxHeader,
  },
};
</script>

<style lang="scss">
@import "./assets/sass/_base.scss";
</style>
