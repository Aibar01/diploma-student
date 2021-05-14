<template>
  <div v-if="Boolean(classes.results.length)">
    <p class="h1 pl-12 pt-8">Shared classes</p>
    <VueSlickCarousel v-bind="settings">
      <SharedClassCard
        v-for="item in classes.results"
        :key="item.id"
        :item="item"
      />
    </VueSlickCarousel>
  </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
import SharedClassCard from './SharedClassCard'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
  components: {
    SharedClassCard,
    VueSlickCarousel,
  },
  props: {
    classes: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      settings: {
        centerMode: true,
        arrows: true,
        dots: false,
        infinite: true,
        initialSlide: 3,
        speed: 500,
        slidesToShow: 4,
        slidesToScroll: 1,
        swipeToSlide: true,
        responsive: [
          {
            breakpoint: 1124,
            settings: {
              slidesToShow: 3,
              slidesToScroll: 3,
              infinite: true,
            },
          },
          {
            breakpoint: 850,
            settings: {
              slidesToShow: 2,
              slidesToScroll: 2,
              initialSlide: 2,
            },
          },
          {
            breakpoint: 600,
            settings: {
              slidesToShow: 1,
              slidesToScroll: 1,
            },
          },
        ],
      },
    }
  },
}
</script>
