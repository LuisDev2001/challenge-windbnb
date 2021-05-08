<template>
  <div
    :class="{
      search: true,
      'is-active': isOpen,
    }"
    ref="jsSearch"
  >
    <div class="search__modal--title">
      <h4>Edit your search</h4>
      <button @click="handleCloseModalSearch()">
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
          autocomplete="off"
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
          autocomplete="off"
          placeholder="Add guests"
        />
        <span class="search__input--placeholder">Guests</span>
      </label>
      <div
        :class="{
          search__button: true,
          'is-active': isOpen,
        }"
        @click="handleOpenModalSearch()"
      >
        <font-awesome-icon icon="search" />
        <span v-if="isOpen" class="search__button--text">Search</span>
      </div>
    </form>
  </div>
  <div
    :class="{
      overlay: true,
      'is-active': isOpen,
    }"
    ref="jsOverlay"
  ></div>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";
import { faSearch, faTimes } from "@fortawesome/free-solid-svg-icons";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

import { reactive, ref, toRefs } from "vue";
library.add(faSearch, faTimes);

export default {
  name: "PxSearch",
  components: {
    FontAwesomeIcon,
  },
  props: {},
  setup() {
    const jsSearch = ref(null);

    const modal = reactive({
      isOpen: false,
    });

    // Event for appear modal search
    const handleOpenModalSearch = () => {
      modal.isOpen = true;
    };

    // Event for disappear modal search
    const handleCloseModalSearch = () => {
      modal.isOpen = false;
    };

    return {
      jsSearch,
      handleOpenModalSearch,
      handleCloseModalSearch,
      ...toRefs(modal),
    };
  },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/sass/components/Header/_PxSearch.scss";
</style>
