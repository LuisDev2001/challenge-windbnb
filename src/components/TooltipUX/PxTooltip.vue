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
    background: rgba(98, 134, 233, 0.3);
    p {
      color: rgba(12, 58, 184, 0.8);
    }
  }
  &.warn {
    background: rgba(237, 248, 77, 0.3);
    p {
      color: rgba(197, 209, 29, 0.3);
    }
  }
  &.error {
    background: rgba(248, 77, 77, 0.8);
    p {
      color: rgba(219, 35, 35, 0.8);
    }
  }
}
</style>
