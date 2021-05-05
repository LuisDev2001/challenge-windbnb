<template>
  <article class="card">
    <div class="card__image">
      <img src="@/assets/img/imagen1.png" alt="Imagen" />
    </div>
    <section class="card__details">
      <section class="card__information">
        <span class="card__type--host">
          Super host
        </span>
        <span class="card__type--private" v-if="false">
          Private room
        </span>
        <span class="card__title">Entire apartment . 2 beds</span>
      </section>
      <div class="card__stars">
        <font-awesome-icon icon="star" />
        <span class="card__stars--points">4.40</span>
      </div>
    </section>
    <div class="card__descripton">
      Stylist apartment in center of the city
    </div>
  </article>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";
import { faStar } from "@fortawesome/free-solid-svg-icons";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
library.add(faStar);

export default {
  name: "PxCard",
  components: {
    FontAwesomeIcon,
  },
};
</script>

<style scoped lang="scss">
@import "~@/assets/sass/components/Card/_PxCard.scss";
</style>
