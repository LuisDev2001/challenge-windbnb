<template>
  <div
    :class="{
      tooltip: true,
      info: info,
      warn: warn,
      error: error,
      'is-active': appear,
    }"
    :style="{
      top: `${top}px`,
      left: `${left}px`,
    }"
  >
    <p v-text="msgTooltip"></p>
  </div>
</template>

<script>
export default {
  name: "PxTooltip",
  props: {
    msgTooltip: String,
    appear: Boolean,
    info: Boolean,
    warn: Boolean,
    error: Boolean,
    top: Number,
    left: Number,
  },
};
</script>

<style lang="scss" scoped>
.tooltip {
  width: auto;
  height: 30px;
  background: #ffffff;
  padding: 4px 8px;
  border-radius: 4px;
  color: #333333;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  display: none;
  box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.3);
  p {
    font-size: 14px;
    font-family: "Montserrat-Bold";
  }
  &.is-active {
    display: inline-flex;
    animation-name: fade;
    animation-duration: 0.5s;
  }
  &.info {
    background: rgb(195, 208, 243);
    p {
      color: rgba(12, 58, 184, 0.8);
    }
  }
  &.warn {
    background: rgb(236, 241, 152);
    p {
      color: rgba(197, 209, 29, 0.3);
    }
  }
  &.error {
    background: rgb(247, 142, 142);
    p {
      color: rgba(219, 35, 35, 0.8);
    }
  }
}
</style>
