<template>
  <div class="gallery">
    <div
      v-for="(slide, index) in slides"
      :key="index"
      :class="{ 'gallery__slide--active' : slideActive === index + 1}"
      class="gallery__slide"
    >
      <img :src="slide.img" class="gallery__img" :alt="`Slide-${index}`">
      <div class="gallery__text">{{ slide.text }}</div>
    </div>

    <div class="gallery-dots">
      <button
        v-for="(item, index) in getSlidesCount"
        :key="index"
        type="button"
        class="gallery-dots__item"
        :class="{ 'gallery-dots__item--active' : slideActive === index + 1}"
        @click="goToSlide(index + 1)"
      />
    </div>

    <button
      class="gallery__btn gallery__btn--prev"
      @click="prevSlide"
      aria-label="Prev slide"
    />
    <button
      class="gallery__btn gallery__btn--next"
      @click="nextSlide"
      aria-label="Next slide"
    />
  </div>
</template>

<script>
export default {
  props: {
    slides: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {
      slideActive: 1
    }
  },
  computed: {
    getSlidesCount() {
      return this.slides?.length;
    }
  },
  methods: {
    prevSlide() {
      this.slideActive--;
      if (this.slideActive < 1) this.slideActive = this.getSlidesCount;
    },
    nextSlide() {
      this.slideActive++;
      if (this.slideActive > this.getSlidesCount) this.slideActive = 1;
    },
    goToSlide(index) {
      this.slideActive = index;
    }
  }
}
</script>

<style lang="scss">
.gallery {
  position: relative;
  margin-top: 34px;
  height: 367px;

  @media (max-width: 767px) {
    height: 300px;
    width: calc(100% + 32px);
    margin-top: 0;
    margin-left: -16px;
  }

  &__slide {
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
    transition: all .5s;
  }

  &__slide--active {
    opacity: 1;
  }

  &__img {
    width: 100%;
    height: 367px;
    object-fit: cover;

    @media (max-width: 767px) {
      height: 300px;
    }
  }

  &__text {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    text-align: center;
    color: #fff;
    font-size: 50px;
    line-height: 1;
  }

  &__btn {
    position: absolute;
    top: 50%;
    background-repeat: no-repeat;
    background-color: transparent;
    width: 30px;
    height: 30px;
    border: 0;
    transform: translateY(-50%);
    cursor: pointer;
    transition: all .3s;

    &:hover {
      transform: translateY(-50%) scale(1.2);
    }
  }

  &__btn--next {
    right: 22px;
    background-image: url("data:image/svg+xml,%3Csvg width='30' height='30' viewBox='0 0 30 30' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Crect x='0.5' y='0.5' width='29' height='29' rx='14.5' fill='white' stroke='%23497952'/%3E%3Cline y1='-1' x2='7.81025' y2='-1' transform='matrix(-0.640184 0.768221 0.768221 0.640184 20 15)' stroke='%23497952' stroke-width='2'/%3E%3Cline x1='19.2318' y1='15.6402' x2='14.2318' y2='9.64018' stroke='%23497952' stroke-width='2'/%3E%3C/svg%3E%0A");
  }

  &__btn--prev {
    left: 22px;
    background-image: url("data:image/svg+xml,%3Csvg width='30' height='30' viewBox='0 0 30 30' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Crect x='0.5' y='0.5' width='29' height='29' rx='14.5' fill='white' stroke='%23497952'/%3E%3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M11 15L16 9L17.5364 10.2804L13.6034 15L17.5364 19.7196L16 21L11 15Z' fill='%23497952'/%3E%3C/svg%3E%0A");
  }

  &-dots {
    position: absolute;
    top: auto;
    left: 0;
    right: 0;
    text-align: center;
    bottom: 24px;
  }

  &-dots__item {
    width: 10px;
    height: 10px;
    border-radius: 100%;
    background-color: #fff;
    border: 0;
    margin-right: 30px;
    transition: all .3s;
    cursor: pointer;

    &:last-child {
      margin-right: 0;
    }

    &:hover {
      background-color: #497952;
    }
  }

  &-dots__item--active {
    background-color: #497952;
  }
}
</style>