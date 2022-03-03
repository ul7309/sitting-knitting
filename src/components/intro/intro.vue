<template>
  <div class="intro">
    <h2 class="h2 intro__title">{{ intro.title }}</h2>
    <p class="intro__text">{{ intro.text }}</p>
    <div class="intro__video">
      <iframe
        :src="intro.src"
        title="YouTube video player"
        frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    intro: {
      type: Object,
      default: () => {}
    }
  },
}
</script>

<style lang="scss">
.intro {
  margin-top: 76px;
  display: flex;
  flex-wrap: wrap;

  @media (max-width: 1023px) {
    flex-direction: column;
    align-items: center;
  }

  &__title {
    margin-bottom: 9px;
    width: 100%;

    @media (max-width: 1023px) {
      text-align: center;
    }
  }

  &__text {
    max-width: 539px;

    @media (max-width: 1023px) {
      width: 100%;
    }
  }

  &__video {
    width: calc(100% - 559px);
    margin-left: 20px;

    @media (max-width: 1023px) {
      margin-top: 20px;
      width: 100%;
      margin-left: 0;
      text-align: center;
    }

    iframe {
      width: 100%;
      height: 315px;
    }
  }
}
</style>