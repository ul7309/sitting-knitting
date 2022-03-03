<template>
  <header class="header">
    <div class="container">
      <div class="header__row">
        <div class="header__item header__logo">
          <img src="../../assets/img/logo.png" alt="Logo" />
        </div>

        <div class="header__item header__location" v-html="header.address" />

        <div class="header__item header__work-time" v-html="header.workTime" />

        <div class="header__item header__phones">
          <a
            v-for="(item, index) in header.phones"
            :key="index"
            :href="item.phone" class="header__phone"
          >
            {{ item.phone }}
          </a>
        </div>

        <div class="header__item header__basket" />

        <div class="header__item header__burger">
          <button
            class="header__burger-btn"
            :class="{ 'header__burger-btn--active' : isVisibleMenu }"
            type="button"
            aria-label="Открыть меню"
            @click="toggleMenu"
          />
        </div>
      </div>
    </div>

    <Navigation
      v-if="isNavigations"
      :navigation="navigation"
      :class="{ 'navigation--open': isVisibleMenu }"
    />
  </header>
</template>

<script>
import Navigation from './navigation'

export default {
  components: {
    Navigation
  },
  props: {
    navigation: {
      type: Array,
      default: () => []
    },
    header: {
      type: Object,
      default: () => {}
    }
  },
  data() {
    return {
      isVisibleMenu: false
    }
  },
  computed: {
    isNavigations() {
      return this.navigation?.length > 1;
    }
  },
  methods: {
    toggleMenu() {
      this.isVisibleMenu = !this.isVisibleMenu;
    }
  }
}
</script>

<style scoped lang="scss">
.header {
  padding-top: 30px;
  position: relative;

  @media (max-width: 767px) {
    padding-top: 12px;
  }

  &__row {
    display: flex;
    align-items: center;
    justify-content: space-between;

    @media (max-width: 767px) {
      flex-wrap: wrap;
    }
  }

  &__item {
    position: relative;
    padding-left: 47px;

    @media (max-width: 1023px) {
      padding-left: 0;
    }

    @media (max-width: 767px) {
        margin-bottom: 10px;
        padding-left: 35px;
    }
  }

  &__logo {
    padding-left: 0;
  }

  &__location {
    background-image: url('../../assets/img/location.png');
    background-repeat: no-repeat;
    background-size: 30px;

    @media (max-width: 1023px) {
      background-image: none;
    }

    @media (max-width: 767px) {
      display: none;
    }
  }

  &__work-time {
    background-image: url('../../assets/img/time.png');
    background-repeat: no-repeat;
    background-size: 35px;

    @media (max-width: 1023px) {
      background-image: none;
    }

    @media (max-width: 767px) {
      display: none;
    }
  }

  &__phones {
    background-image: url('../../assets/img/phone.png');
    background-repeat: no-repeat;
    background-size: 30px;

    @media (max-width: 1023px) {
      background-image: none;
    }

    @media (max-width: 767px) {
      margin-right: 50px;
    }
  }

  &__phone {
    display: block;
    color: #535353;
    text-decoration: none;
    transition: all .3s;

    &:hover {
      opacity: .5;
    }
  }

  &__basket {
    background-image: url('../../assets/img/basket.png');
    background-repeat: no-repeat;
    background-size: 35px;
    width: 35px;
    height: 35px;
    padding-left: 0;

    @media (max-width: 767px) {
      position: absolute;
      top: 30px;
      right: 16px;
      min-height: 30px;
    }
  }

  &__burger {
    display: none;

    @media (max-width: 767px) {
      position: absolute;
      top: 30px;
      right: 16px;
      padding-left: 0;
      z-index: 2;
    }
  }

  &__burger-btn {
    font-size: 0;
    border: 0;
    background-image: url("data:image/svg+xml,%3Csvg version='1.1' fill='%23538059' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' x='0px' y='0px' viewBox='0 0 250.579 250.579' style='enable-background:new 0 0 250.579 250.579;' xml:space='preserve'%3E%3Cpath style='fill-rule:evenodd;clip-rule:evenodd;' d='M22.373,76.068h205.832c12.356,0,22.374-10.017,22.374-22.373 c0-12.356-10.017-22.373-22.374-22.373H22.373C10.017,31.323,0,41.339,0,53.696C0,66.052,10.017,76.068,22.373,76.068z M228.205,102.916H22.373C10.017,102.916,0,112.933,0,125.289c0,12.357,10.017,22.373,22.373,22.373h205.832 c12.356,0,22.374-10.016,22.374-22.373C250.579,112.933,240.561,102.916,228.205,102.916z M228.205,174.51H22.373 C10.017,174.51,0,184.526,0,196.883c0,12.356,10.017,22.373,22.373,22.373h205.832c12.356,0,22.374-10.017,22.374-22.373 C250.579,184.526,240.561,174.51,228.205,174.51z'/%3E%3C/svg%3E%0A");
    background-repeat: no-repeat;
    background-color: transparent;
    width: 30px;
    height: 30px;

    &--active {
      background-image: url("data:image/svg+xml,%3Csvg version='1.1' fill='%23FFFFFF' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' x='0px' y='0px' viewBox='0 0 250.579 250.579' style='enable-background:new 0 0 250.579 250.579;' xml:space='preserve'%3E%3Cpath style='fill-rule:evenodd;clip-rule:evenodd;' d='M22.373,76.068h205.832c12.356,0,22.374-10.017,22.374-22.373 c0-12.356-10.017-22.373-22.374-22.373H22.373C10.017,31.323,0,41.339,0,53.696C0,66.052,10.017,76.068,22.373,76.068z M228.205,102.916H22.373C10.017,102.916,0,112.933,0,125.289c0,12.357,10.017,22.373,22.373,22.373h205.832 c12.356,0,22.374-10.016,22.374-22.373C250.579,112.933,240.561,102.916,228.205,102.916z M228.205,174.51H22.373 C10.017,174.51,0,184.526,0,196.883c0,12.356,10.017,22.373,22.373,22.373h205.832c12.356,0,22.374-10.017,22.374-22.373 C250.579,184.526,240.561,174.51,228.205,174.51z'/%3E%3C/svg%3E%0A");
    }
  }
}

</style>
