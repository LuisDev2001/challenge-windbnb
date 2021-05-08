<template>
  <label class="search__label">
    <input
      type="text"
      :id="id"
      :name="name"
      class="search__input"
      autocomplete="off"
      :placeholder="placeholder"
    />
    <span class="search__input--placeholder">{{ placeholderTextMobile }}</span>
  </label>
</template>

<script>
export default {
  name: "PxInput",
  props: {
    id: String,
    name: String,
    placeholder: String,
    placeholderTextMobile: String,
  },
};
</script>

<style lang="scss" scoped>
.search__label {
  display: flex;
  justify-content: center;
  align-items: center;
  flex: 1;
  height: 100%;
  border-radius: 16px;
  &.focus {
    border: 1px solid #333333;
  }
  &__label:first-child {
    .search__input {
      border-right: 1px solid #f2f2f2;
    }
  }
  .search__input--placeholder {
    display: none;
  }
  .search__input {
    display: flex;
    justify-content: center;
    align-items: center;
    flex: 1;
    height: 100%;
    border-radius: 16px;
    border: 0;
    padding: 16px;
    margin: 0;
    width: 100%;
    font-family: "Mulish-Regular";
    border-radius: 16px;
    &::placeholder {
      font-family: "Mulish-Regular";
      color: #bdbdbd;
    }
  }

  @media screen and (min-width: 992px) {
    width: 30%;
  }
  @media screen and (min-width: 1200px) {
    width: 40%;
  }
}
.search.is-active {
  .search__label {
    display: block;
    width: 100%;
    position: relative;
    padding: 12px 0 0;
    &:first-child {
      border-bottom: 1px solid #f2f2f2;
    }
  }
  .search__input--placeholder {
    display: block;
    position: absolute;
    top: 12px;
    left: 16px;
    z-index: 10;
    font-size: 11px;
    font-family: "Mulish-Bold";
    font-weight: 800;
    color: #333333;
  }
}
</style>
