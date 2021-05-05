<template>
  <div class="search">
    <label class="search__label">
      <input
        type="text"
        id="location"
        name="location"
        class="search__input"
        placeholder="Add location"
      />
      <span class="search__input--placeholder">Location</span>
    </label>
    <label class="search__label">
      <input
        type="text"
        id="guests"
        name="guests"
        class="search__input"
        placeholder="Add guests"
      />
      <span class="search__input--placeholder">Guests</span>
    </label>
    <div class="search__icon">
      <font-awesome-icon icon="search" />
    </div>
  </div>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";
import { faSearch } from "@fortawesome/free-solid-svg-icons";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
library.add(faSearch);

export default {
  name: "PxSearch",
  components: {
    FontAwesomeIcon,
  },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/sass/components/Header/_PxSearch.scss";
</style>
