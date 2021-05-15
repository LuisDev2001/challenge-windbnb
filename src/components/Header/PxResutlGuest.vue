<template>
  <section
    :class="{
      result: true,
      'result-guest': true,
      'is-active': appear,
    }"
  >
    <h2>PxResutlGuest</h2>
  </section>
</template>

<script>
export default {
  name: "PxResutlGuest",
  props: {
    appear: Boolean,
  },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/sass/components/Header/_PxResutlGuest.scss";
</style>
