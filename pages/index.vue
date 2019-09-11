<template>
  <v-layout column justify-center align-center>
    <v-flex>
      <v-carousel
        hide-delimiters
        cycle
        class="d-md-flex d-lg-flex"
        :height="height"
        v-if="carouselMounted"
      >
        <v-carousel-item
          v-for="item in items"
          :key="item.title"
          :src="item.src"
          gradient="to top right, rgba(100,100,100,.70), rgba(0,0,0,.0)"
          :width="width"
        >
          <v-container class="ma-0 pl-10 fill-height">
            <v-card class="ma-10 pl-12" tile color="transparent" elevation="0">
              <v-card-title class="display-2">{{ item.title }}</v-card-title>
              <v-card-text class="headline">{{ item.content }}</v-card-text>
            </v-card>
          </v-container>
        </v-carousel-item>
      </v-carousel>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          src: '../wire_main1.jpg',
          title: 'Global EDM Leader',
          content: 'EDM 와이어의 글로벌 리더'
        },
        {
          src: '../wire_main2.jpg',
          title: 'Best Quality & Service',
          content: '최고의 제품과 최고의 서비스'
        },
        {
          src: '../wire_main3.jpg',
          title: 'Continuous Development',
          content: '더 나은 미래를 위한 끊임없는 개발'
        }
      ],
      width: 0,
      height: 0,
      carouselMounted: false
    }
  },
  methods: {
    handleResize: function() {
      this.width = window.innerWidth
      this.height = window.innerHeight - 160
    }
  },
  mounted: function() {
    this.width = window.innerWidth
    this.height = window.innerHeight - 160
    this.carouselMounted = true
    window.addEventListener('resize', this.handleResize)
  },
  beforeDestroy: function() {
    window.removeEventListener('resize', this.handleResize)
  }
}
</script>

<style scoped>
.bottom-gradient {
  background-image: linear-gradient(
    to top,
    rgba(0, 0, 0, 0.4) 0%,
    transparent 72px
  );
}

.repeating-gradient {
  background-image: repeating-linear-gradient(
    -45deg,
    rgba(255, 0, 0, 0.25),
    rgba(255, 0, 0, 0.25) 5px,
    rgba(0, 0, 255, 0.25) 5px,
    rgba(0, 0, 255, 0.25) 10px
  );
}
</style>