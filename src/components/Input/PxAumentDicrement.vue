<template>
  <section class="aument-dicrement">
    <section class="aument-dicrement-type">
      <b>{{ typePerson }}</b>
      <p>{{ age }}</p>
    </section>
    <section class="aument-dicrement-actions">
      <button @click="handleDicrementQuantity()">-</button>
      <input type="number" ref="jsInputQuantity" v-model="quantity" />
      <button @click="handleAumentQuantity()">+</button>
    </section>
  </section>
</template>

<script>
import { reactive, toRefs } from "vue";
export default {
  name: "PxAumentDicrement",
  props: {
    typePerson: String,
    age: String,
  },
  setup() {
    const aumentDicrementOptionAPI = reactive({
      quantity: 0,
    });

    const handleAumentQuantity = () => {
      aumentDicrementOptionAPI.quantity++;
      if (aumentDicrementOptionAPI.quantity > 99) {
        aumentDicrementOptionAPI.quantity = 99;
      }
    };

    const handleDicrementQuantity = () => {
      aumentDicrementOptionAPI.quantity--;
      if (aumentDicrementOptionAPI.quantity <= 0) {
        aumentDicrementOptionAPI.quantity = 0;
      }
    };

    return {
      ...toRefs(aumentDicrementOptionAPI),
      handleAumentQuantity,
      handleDicrementQuantity,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/sass/components/Input/_PxAumentDicrement.scss";
</style>
