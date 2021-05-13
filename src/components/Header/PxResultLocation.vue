<template>
  <section
    :class="{
      'result-location': true,
      'is-active': appear,
    }"
  >
    <ul class="result-location__list">
      <li
        class="result-location__item"
        v-for="(result, index) in resultList"
        :key="index"
      >
        <font-awesome-icon icon="map-marker-alt" />
        {{ result }}
      </li>
    </ul>
  </section>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";
import { faMapMarkerAlt } from "@fortawesome/free-solid-svg-icons";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
library.add(faMapMarkerAlt);

export default {
  name: "PxResultLocation",
  components: {
    FontAwesomeIcon,
  },
  props: {
    appear: Boolean,
    resultList: Array,
  },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/sass/components/Header/_PxResultLocation.scss";
</style>
