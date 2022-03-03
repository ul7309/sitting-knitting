<template>
  <nav class="navigation">
    <a
      v-for="(item, index) in navigation"
      :key="index" 
      :href="item.link"
      class="navigation__link"
    >
      {{ item.name }}
    </a>
  </nav>
</template>

<script>
export default {
  props: {
    navigation: {
      type: Array,
      default: () => []
    }
  },
}
</script>

<style lang="scss">
.navigation {
  background-color: #497952;
  margin-top: 19px;
  padding: 10px 0;
  text-align: center;

  @media (max-width: 767px) {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    margin-top: 0;
    padding-top: 100px;
    height: 100vh;
    z-index: 1;
    display: none;
  }

  &--open {
    display: block;
  }

  &__link {
    color: #FFF;
    text-decoration: none;
    margin-right: 30px;
    display: inline-block;
    font-weight: 700;
    font-size: 14px;
    line-height: 19px;
    transition: all .3s;

    @media (max-width: 1023px) {
      margin-right: 20px;
    }

    @media (max-width: 767px) {
      display: block;
      margin-right: 0;
      margin-bottom: 10px;
    }

    &:last-child {
      margin-right: 0;
    }

    &:hover {
      opacity: .5;
    }
  }
}
</style>