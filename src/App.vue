<template>
  <div id="app">
    <Header :navigation="navigation" :header="header" />

    <div class="container">
      <Gallery v-if="isVisibleGallery" :slides="slides" />

      <Features v-if="isVisibleFeatures" :features="features" />

      <Intro v-if="isVisibleIntro" :intro="intro" />
    </div>
  </div>
</template>

<script>
import Header from './components/header/header';
import Gallery from './components/gallery/gallery';
import Features from './components/features/features';
import Intro from './components/intro/intro';

export default {
  name: 'App',
  components: {
    Header,
    Gallery,
    Features,
    Intro
  },
  data() {
    return {
      header: {
        address: 'м. Кропоткинская<br>Соймоновский проезд, д.7 с.1',
        workTime: 'Пн - Пт 11 - 20<br>Сб - Вск 11 - 18',
        phones: [
          {
            phone: '+7 800 000 00 00'
          },
          {
            phone: '+7 800 000 00 00'
          }
        ]
      },
      navigation: [
        {
          name: 'Пряжа',
          link: "#"
        },
        {
          name: 'Спицы',
          link: "#"
        },
        {
          name: 'Крючки',
          link: "#"
        },
        {
          name: 'Аксессуары',
          link: "#"
        },
        {
          name: 'Подарочные сертификаты',
          link: "#"
        },
        {
          name: 'МК и описания',
          link: "#"
        },
        {
          name: 'Модели',
          link: "#"
        }
      ],
      slides: [
        {
          img: "https://monosnap.com/image/l7J3WWfIabwG3z5ON0XWc3Ybh2QOEh",
          text: "Slide 1"
        },
        {
          img: "https://monosnap.com/image/l7J3WWfIabwG3z5ON0XWc3Ybh2QOEh",
          text: "Slide 2"
        },
        {
          img: "https://monosnap.com/image/l7J3WWfIabwG3z5ON0XWc3Ybh2QOEh",
          text: "Slide 3"
        }
      ],
      features: [
        {
          img: "https://monosnap.com/image/wY0Te6VqLs2XWOID8ORYh5IDvqEty3",
          text: "Только <br>натуральный состав"
        },
        {
          img: "https://monosnap.com/image/ywm3x9uzSpyufvMCfSakPwwba14fDY",
          text: "Актуальное <br>наличие на сайте"
        },
        {
          img: "https://monosnap.com/image/DMZBTS4i4HdRQ1rURYqUwfE8B7ygyb",
          text: "Быстрая <br>отправка"
        },
        {
          img: "https://monosnap.com/image/Subd9L07Cc6XQz8D12ZLxoXd54lk4X",
          text: "Удобное <br>расположение"
        },
        {
          img: "https://monosnap.com/image/408gGD5cz3cF1Y5w80o4wAC6mcpMkI",
          text: "Помощь <br>в подборе товаров"
        }
      ],
      intro: {
        title: "ДОБРО ПОЖАЛОВАТЬ В НАШ НОВЫЙ МАГАЗИН!",
        text: "Мы садимся вязать, и вселенная вокруг начинает жить по-другому. Точнее, мы создаем собственную вселенную, в которой мы отдыхаем, вдохновляемся и создаем шедевры. Наш магазин за то, чтобы вы занимались своим любимым делом с удовольствием. Наш магазин – это место, где вам предложат пряжу и инструмент исключительного качества для создания лучших творений, которые вы только задумали. Наш магазин – это место, куда вы просто можете прийти поболтать и выпить чашечку кофе за вязанием",
        video: "https://www.youtube.com/embed/RK1K2bCg4J8"
      }
    }
  },
  computed: {
    isVisibleGallery() {
      return this.slides?.length > 0;
    },
    isVisibleFeatures() {
      return this.features?.length > 0;
    },
    isVisibleIntro() {
      if (!this.intro) return false;

      return Object.keys(this.intro).length > 0;
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: 'Open Sans', sans-serif;
  font-weight: 400;
  font-style: normal;
  color: #535353;
  font-size: 14px;
  line-height: 19px;
}

button {
  padding: 0;
}

h2, .h2 {
  font-weight: bold;
  font-size: 16px;
  line-height: 22px;
  color: #535353;
}

p {
  font-size: 12px;
  line-height: 20px;
  color: #535353;
}

.container {
  margin: 0 auto;
  max-width: 1110px;
  width: 100%;
  padding-left: 45px;
  padding-right: 45px;

  @media (max-width: 767px) {
    padding-left: 16px;
    padding-right: 16px;
  }
}
</style>
