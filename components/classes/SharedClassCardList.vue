<template>
  <div>
    <p class="h1 pt-8">Shared classes</p>
    <VueSlickCarousel v-bind="settings">
      <SharedClassCard v-for="item in items" :key="item" />
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
  data() {
    return {
      items: [1, 2, 3, 4, 5, 6, 7, 8],
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
