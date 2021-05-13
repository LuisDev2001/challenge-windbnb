<template>
  <label
    :class="{
      search__label: true,
    }"
    ref="jsLabel"
  >
    <input
      type="text"
      :id="id"
      :name="name"
      class="search__input"
      @click="handleFocusInput()"
      autocomplete="off"
      ref="jsInput"
      :placeholder="placeholder"
    />
    <span class="search__input--placeholder">{{ placeholderTextMobile }}</span>
  </label>
</template>

<script>
import { reactive, ref, toRefs } from "vue";
export default {
  name: "PxInput",
  props: {
    id: String,
    name: String,
    placeholder: String,
    placeholderTextMobile: String,
  },
  setup() {
    const jsInput = ref(null);

    const handleFocusInput = () => {
      jsInput.value.focus();
    };

    return {
      handleFocusInput,
      jsInput,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/sass/components/Input/_input.scss";
</style>
