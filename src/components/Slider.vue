<template id="slider-template">
  <div class="slider-wrap">
    <div class="slider">
      <transition-group name="slide-fade">
        <!-- Slider Item -->
        <div
          class="slider__item"
          v-for="(item, index) in sliders"
          :key="index"
          v-show="item.active"
          :style="`background-image: url('${item.image}');`"
        >
          <!-- Slider content -->
          <div class="slider-content">
            <div class="keywords">{{ item.keyWords }}</div>
            <h2 class="title">{{ item.title }}</h2>
            <p class="description">{{ item.description }}</p>
          </div>
        </div>
      </transition-group>
    </div>
    <!-- Slider Navigation -->
    <ul class="slider__nuv">
      <li
        v-for="(item, index) in sliders"
        :key="index"
        @click="currentSlide = index; activeItem(index)"
        :class="item.active ? 'active_nuv' : ''"
      ></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Slider",

  template: "#slider-template",
  data: function() {
    return {
      currentSlide: 1, // Current SLide
      slideInterval: 10000, // Interval bentween slide animations
      sliders: [
        {
          image: "img/slider-img.png",
          keyWords: "|  Design+Lifestyle  |  Smart Living  |",
          title:
            "Was hilft mir, Energie zu sparen und Spaß zu haben, bei mir zu Hause?",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut  dolor in reprehenderit in quia...",
          active: false
        },
        {
          image: "img/slider-img.png",
          keyWords: "|  Design+Lifestyle  |  Smart Living  |",
          title: "some text",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut  dolor in reprehenderit in quia...",
          active: false
        },
        {
          image: "img/slider-img.png",
          keyWords: "|  Design+Lifestyle  |  Smart Living  |",
          title: "some text",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut  dolor in reprehenderit in quia...",
          active: false
        },
        {
          image: "img/slider-img.png",
          keyWords: "|  Design+Lifestyle  |  Smart Living  |",
          title: "some text",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut  dolor in reprehenderit in quia...",
          active: false
        },
        {
          image: "img/slider-img.png",
          keyWords: "|  Design+Lifestyle  |  Smart Living  |",
          title: "some text",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut  dolor in reprehenderit in quia...",
          active: false
        },
        {
          image: "img/slider-img.png",
          keyWords: "|  Design+Lifestyle  |  Smart Living  |",
          title: "some text",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut  dolor in reprehenderit in quia...",
          active: false
        }
      ]
    };
  },
  created: function() {
    let activeSlide = this.sliders[this.currentSlide - 1]; // define active slide
    activeSlide.active = true; // set active property true

    setInterval(() => {
      // Set interval function
      this.startSlider(this.currentSlide);
    }, this.slideInterval);
  },
  methods: {
    // Start slider animation
    startSlider: function(currentSlide) {
      if (currentSlide < this.sliders.length - 1) {
        this.currentSlide++;
      } else {
        this.currentSlide = 0;
      }
      this.activeItem(currentSlide);
    },
    // Set active property for current slide element
    activeItem: function(index) {
      for (let i = 0; i < this.sliders.length; i++) {
        this.sliders[i].active = false;
      }
      this.sliders[index].active = true;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass">
.slider-wrap
  height: 100%
  position: relative
.slider
  width: 100%
  height: 100%
  overflow: hidden
  z-index: 10
  &__item
    display: flex
    align-items: center
    height: 100%
    background-size: cover
    background-position: center
    color: #ffffff
    .slider-content
      max-width: 420px
      margin: 20px auto 0
      .keywords
        font-family: 'Muli', sans-serif
        font-size: 13px
        text-transform: uppercase
      .title
        margin: 30px 0 35px
        font-family: 'Muli', sans-serif
        font-weight: normal
        font-size: 22px
        line-height: 1.2
      .description
        font-size: 14px
        line-height: 1.5
  &__nuv
    position: absolute
    bottom: 0
    left: 0
    right: 0
    padding-left: 0
    margin-top: 15px
    display: flex
    justify-content: center
    margin-bottom: 20px
    list-style-type: none
    z-inedx: 20
    li.active_nuv
      background-color: #ffffff
    li
      margin-right: 20px
      cursor: pointer
      width: 4px
      height: 4px
      transition: all .25s ease
      background-color: #8f9290
      &:hover
        background-color: #35475F

.slide-fade-enter-active
  transition: all .3s ease

.slide-fade-leave-active
  transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0)

.slide-fade-enter,
.slide-fade-leave-to
  transform: translateX(10px)
  opacity: 0
</style>
