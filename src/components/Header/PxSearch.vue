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
        v-model:valueInput="inputLocationValue"
        @click="handleOpenResultLocation()"
      />
      <PxInput
        id="guests"
        name="guests"
        placeholder="Add guests"
        placeholderTextMobile="Guests"
        v-model:valueInput="inputGuestValue"
        @click="handleOpenGuestLocation()"
      />
      <div
        :class="{
          search__button: true,
        }"
        @click="handleOpenModalSearch()"
      >
        <font-awesome-icon icon="search" />
        <span v-if="isOpen" class="search__button--text">Search</span>
      </div>
      <div
        :class="{
          'search__button search-mode': true,
        }"
      >
        <font-awesome-icon icon="search" />
        <span v-if="isOpen" class="search__button--text">Search</span>
      </div>
    </form>
    <section
      :class="{
        search__result: true,
        'is-active': isOpen,
      }"
    >
      <!-- component result location -->
      <PxResultLocation
        :appear="openLocationContainer"
        :resultList="resultLocation"
      />
      <!-- component result guest  -->
      <PxResutlGuest :appear="openGuestContainer" />
    </section>
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
import PxResultLocation from "@/components/Header/PxResultLocation";
import PxResutlGuest from "@/components/Header/PxResutlGuest";

import { reactive, ref, toRefs } from "vue";

export default {
  name: "PxSearch",
  components: {
    FontAwesomeIcon,
    PxInput,
    PxResultLocation,
    PxResutlGuest,
  },
  props: {},
  setup() {
    const jsSearch = ref(null);

    // Boolean variable for appear or dissapear modal search
    const modal = reactive({
      isOpen: false,
    });

    // Result list array for use reactive variable
    const resultLocationOptions = reactive({
      list: [
        "Helsinki, Finland",
        "Turku, Finland",
        "Oulu, Finland",
        "Vaasa, Finland",
        "Lurin, Lima",
        "Pachacamac, Lima",
        "San Juan de Miraflores, Lima",
        "Surco, Lima",
        "San Isidro, Lima",
      ],
      inputLocationValue: "",
      inputGuestValue: "",
      openLocationContainer: false,
      openGuestContainer: false,
      resultLocation: [], //This array is for push result and print in the component
    });

    // Event for appear modal search
    const handleOpenModalSearch = () => {
      modal.isOpen = true;
    };

    // Event for disappear modal search
    const handleCloseModalSearch = () => {
      modal.isOpen = false;
    };

    //Event for appear container result location
    const handleOpenResultLocation = () => {
      resultLocationOptions.openLocationContainer = true;
      resultLocationOptions.openGuestContainer = false;
    };

    //Event for appear container guest location
    const handleOpenGuestLocation = () => {
      resultLocationOptions.openGuestContainer = true;
      resultLocationOptions.openLocationContainer = false;
    };

    return {
      jsSearch,
      handleOpenModalSearch,
      handleCloseModalSearch,
      handleOpenResultLocation,
      handleOpenGuestLocation,
      ...toRefs(modal),
      ...toRefs(resultLocationOptions),
    };
  },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/sass/components/Header/_PxSearch.scss";
</style>
