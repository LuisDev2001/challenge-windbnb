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
      <PxInput
        id="location"
        name="location"
        placeholder="Add location"
        placeholderTextMobile="Location"
      />
      <PxInput
        id="guests"
        name="guests"
        placeholder="Add guests"
        placeholderTextMobile="Guests"
      />
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
library.add(faSearch, faTimes);

//Import component custom - LuisDev2001
import PxInput from "@/components/Input/PxInput";

import { reactive, ref, toRefs } from "vue";

export default {
  name: "PxSearch",
  components: {
    FontAwesomeIcon,
    PxInput,
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
