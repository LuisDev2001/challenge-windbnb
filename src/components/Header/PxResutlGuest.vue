<template>
  <section
    :class="{
      'result result-guest': true,
      'is-active': appear,
    }"
  >
    <PxAumentDicrement typePerson="Adult" age="Ages 13 or above" />
    <PxAumentDicrement typePerson="Children" age="Ages 2-12" />
  </section>
</template>

<script>
import PxAumentDicrement from "@/components/Input/PxAumentDicrement";
export default {
  name: "PxResutlGuest",
  props: {
    appear: Boolean,
  },
  components: {
    PxAumentDicrement,
  },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/sass/components/Header/_PxResutlGuest.scss";
</style>
