<template>
  <div id="app">
    <!-- Header -->
    <header class="header">
      <!-- Header Logo  -->
      <div class="left-header">
        <a href="#" class="logo">
          <img src="./assets/img/logo.png" alt class="logo-img" />
        </a>
      </div>
      <!-- Header Navigation  -->
      <div class="right-header">
        <!-- Top Navigation -->
        <div class="top-navigation-wrap">
          <nav class="header-top-navigation">
            <a href="#">Über uns</a>
            <a href="#">Redaktion</a>
          </nav>
          <!-- Language Swither -->
          <div class="language-switch">
            <button class="deutch-lang active">de</button>
            <button class="english-lang">en</button>
          </div>
        </div>
        <!-- Bottom Navigation -->
        <div class="bottom-navigation-wrap">
          <input class="header-search-input" type="text" />
          <nav
            class="header-bottom-navigation"
            v-bind:class="{ show: isHidden }"
          >
            <span class="hide-on-mobile">|</span>
            <a href="#">Design+lifestyle</a>
            <span class="hide-on-mobile">|</span>
            <a href="#">Trends</a>
            <span class="hide-on-mobile">|</span>
            <a href="#">Infodelight</a>
            <span class="hide-on-mobile">|</span>
            <a href="#">Smart Living</a>
          </nav>
        </div>
      </div>
      <!-- Mobile Navigation Button-->
      <div class="mobile-nav-btn" v-on:click="isHidden = !isHidden">
        <div></div>
        <div></div>
        <div></div>
      </div>
    </header>
    <!-- First Section -->
    <section class="first-section">
      <div class="left-part">
        <Slider />
      </div>
      <div class="right-part">
        <!-- Welcome Widget -->
        <div class="welcome-widget-wrap">
          <div class="welcome-widget">
            <div class="title">
              A place called Inspiration.
            </div>
            <div class="description">
              Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet,
              consectetur, adipisci velit, sed quia non numquam eius modi
              tempora incidunt ut labore et dolore magnam voluptatem.
            </div>
            <a href="#" class="about-link">Über die Autoren</a>
            <a href="#" class="about-link">Über das magazin</a>
          </div>
        </div>
      </div>
    </section>
    <!-- News Section -->
    <section class="news-section">
      <article class="news-article first-article">
        <div class="article-wrap">
          <div class="keywords">| Design+Lifestyle | Smart Living |</div>
          <h2 class="title">
            Was hilft mir, Energie zu sparen und Spaß zu haben, bei mir zu
            Hause?
          </h2>
          <p class="description">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do
            eiusmod tempor incididunt ut dolor in reprehenderit in quia...
          </p>
        </div>
      </article>
      <article class="news-article second-article">
        <div class="article-wrap">
          <div class="keywords">| Design+Lifestyle | Smart Living |</div>
          <h2 class="title">
            Was hilft mir, Energie zu sparen und Spaß zu haben, bei mir zu
            Hause?
          </h2>
          <p class="description">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do
            eiusmod tempor incididunt ut dolor in reprehenderit in quia...
          </p>
        </div>
      </article>
    </section>
    <!-- Charts Section -->
    <section class="chart-section">
      <div class="pie-chart">
        <PieChart />
      </div>
      <div class="line-chart">
        <CustomChart />
      </div>
    </section>
  </div>
</template>

<script>
import Slider from "./components/Slider.vue";
import PieChart from "./components/PieChart.vue";
import CustomChart from "./components/CustomChart.vue";

export default {
  name: "App",
  components: {
    Slider,
    PieChart,
    CustomChart
  },
  data() {
    return {
      isHidden: false
    };
  }
};
</script>

<style lang="sass">
 /* Import PT Sans Google font instead of "Verdana" and
 import Muli Google font instead of "Linotype"
 */
@import url('https://fonts.googleapis.com/css?family=Muli:400,700|PT+Sans:400,700&display=swap')

// Import main styles
@import "./sass/index.sass"
</style>
