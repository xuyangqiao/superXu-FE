<template>
  <div class="container">
    <div v-swiper:mySwiper="swiperOption">
      <div class="swiper-wrapper">
        <div class="swiper-slide" v-for="(item, index) in bannerList" :key="index">
          <img :src="item.url">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  components: {},

  async asyncData () {
    let data = await axios.get('/api/test?id=1&name=xuyangqiao')
    console.log(data)
    return {
      bannerList: data.images
    }
  },

  data () {
    return {
      swiperOption: {
        loop: true,
        slidesPerView: 'auto',
        centeredSlides: true,
        spaceBetween: 30
      },
      bannerList: []
    }
  }
}
</script>

<style lang="scss">

</style>
