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
        @mouseenter="handleOpenTooltip($event)"
      >
        <font-awesome-icon icon="cogs" />
        <span v-if="isOpen" class="search__button--text">Search</span>
        <PxTooltip
          msgTooltip="Custom search"
          :info="true"
          :appear="false"
          :top="10"
          :left="20"
        />
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
        'is-search-guest': isGuestSelection,
      }"
    >
      <!-- component result location -->
      <PxResultLocation
        :appear="openLocationContainer"
        :resultList="resultFilterLocation"
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
import { faSearch, faTimes, faCogs } from "@fortawesome/free-solid-svg-icons";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
library.add(faSearch, faTimes, faCogs);

//Import component custom - LuisDev2001
import PxInput from "@/components/Input/PxInput";
import PxResultLocation from "@/components/Header/PxResultLocation";
import PxResutlGuest from "@/components/Header/PxResutlGuest";
import PxTooltip from "@/components/TooltipUX/PxTooltip";

import { computed, reactive, ref, toRefs } from "vue";

export default {
  name: "PxSearch",
  components: {
    FontAwesomeIcon,
    PxInput,
    PxResultLocation,
    PxResutlGuest,
    PxTooltip,
  },
  props: {},
  setup() {
    const jsSearch = ref(null);

    // Boolean variable for appear or dissapear modal search
    const modalState = reactive({
      isOpen: false,
    });

    // Use reactive variables for Composition API
    const resultSearchState = reactive({
      list: [
        "Helsinki, Finland",
        "Turku, Finland",
        "Oulu, Finland",
        "Vaasa, Finland",
      ],
      inputLocationValue: "",
      inputGuestValue: "",
      openLocationContainer: false,
      openGuestContainer: false,
      isGuestSelection: false,
      resultLocation: [], //This array is for push result and print in the component
    });

    // Event for appear modal search
    const handleOpenModalSearch = () => {
      modalState.isOpen = true;
      //Disappear guest & location container, when click in oppen modal of advanced search
      resultSearchState.openGuestContainer = false;
      resultSearchState.openLocationContainer = false;
    };

    // Event for disappear modal search
    const handleCloseModalSearch = () => {
      modalState.isOpen = false;
      resultSearchState.isGuestSelection = false;
      resultSearchState.openLocationContainer = false;
      resultSearchState.openGuestContainer = false;
    };

    //Event for appear container result location
    const handleOpenResultLocation = () => {
      //Apear container location result
      resultSearchState.openLocationContainer = true;
      //Dessapear container guest result
      resultSearchState.openGuestContainer = false;
      //This option put the container in the initial position
      resultSearchState.isGuestSelection = false;
    };

    //Event for appear container guest location
    const handleOpenGuestLocation = () => {
      //Apear container guest result
      resultSearchState.openGuestContainer = true;
      //Dessapear container guest result
      resultSearchState.openLocationContainer = false;
      //This option put the option in the place
      resultSearchState.isGuestSelection = true;
    };

    //Event for appear tooltip
    const handleOpenTooltip = (event) => {
      console.log(event);
      console.log(event.y);
      console.log(event.x);
    };

    // Functionality filter list location
    const resultFilterLocation = computed(() => {
      return resultSearchState.list.filter((result) => {
        return result
          .toLowerCase()
          .includes(resultSearchState.inputLocationValue.toLowerCase());
      });
    });

    return {
      jsSearch,
      handleOpenModalSearch,
      handleCloseModalSearch,
      handleOpenResultLocation,
      handleOpenGuestLocation,
      handleOpenTooltip,
      resultFilterLocation,
      ...toRefs(modalState),
      ...toRefs(resultSearchState),
    };
  },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/sass/components/Header/_PxSearch.scss";
</style>
