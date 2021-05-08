<template>
  <div :class="{ search: true, 'is-active': isOpen }" ref="jsSearch">
    <div class="search__modal--title">
      <h4>Edit your search</h4>
      <button>
        <font-awesome-icon icon="times" />
      </button>
    </div>
    <form class="search__form">
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
      <div
        :class="{
          search__button: true,
          'is-active': isOpen,
        }"
      >
        <font-awesome-icon icon="search" />
        <span v-if="isOpen" class="search__button--text">Search</span>
      </div>
    </form>
  </div>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";
import { faSearch, faTimes } from "@fortawesome/free-solid-svg-icons";

import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { onMounted, ref } from "vue";
library.add(faSearch, faTimes);

export default {
  name: "PxSearch",
  components: {
    FontAwesomeIcon,
  },
  props: {},
  setup() {
    const jsSearch = ref(null);
    const isOpen = true;
    onMounted(() => {
      console.log(jsSearch.value);
    });

    return {
      jsSearch,
      isOpen,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/sass/components/Header/_PxSearch.scss";
</style>
