<template>
  <article class="card">
    <div class="card__image">
      <img :src="url" :alt="'Imagen' + id" />
    </div>
    <section class="card__details">
      <section class="card__information">
        <span class="card__type--host" v-if="host">
          Super host
        </span>
        <span class="card__title">
          {{ house }}
        </span>
      </section>
      <div class="card__stars">
        <font-awesome-icon icon="star" />
        <span class="card__stars--points">{{ starsPoints }}</span>
      </div>
    </section>
    <div class="card__descripton">{{ description }}</div>
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
  props: {
    id: Number,
    url: String,
    host: Boolean,
    house: String,
    starsPoints: String,
    description: String,
  },
};
</script>

<style scoped lang="scss">
@import "~@/assets/sass/components/Card/_PxCard.scss";
</style>
