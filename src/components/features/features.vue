<template>
  <div class="features">
    <div
      v-for="(item, index) in features"
      :key="index"
      class="features__item"
    >
      <div class="features__img-wrap">
        <img :src="item.img" class="features__img" :alt="item.text" />
      </div>

      <p class="features__text" v-html="item.text" />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    features: {
      type: Array,
      default: () => []
    }
  },
}
</script>

<style lang="scss">
.features {
  margin-top: 75px;
  display: flex;

  @media (max-width: 767px) {
    flex-wrap: wrap;
    justify-content: center;
  }

  &__item {
    width: 20%;

    @media (max-width: 767px) {
      width: 50%;
    }
  }

  &__img-wrap {
    width: 90px;
    height: 90px;
    margin: 0 auto 24px;
  }

  &__img {
    width: 90px;
    height: 90px;
    object-fit: contain;
  }

  &__text {
    max-width: 210px;
    text-align: center;
    color: #497952;
  }
}
</style>