<template>
  <div class="wrapper">
    <swiper :options="swiperOption" v-if="showSwiper">   <!-- v-if 判断等ajax返回了list 的数据之后再显示swiper -->
      <swiper-slide v-for="item of list" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl"/>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      }
    }
  },
  computed: {
    showSwiper () {
      return this.list.length
    }
  }
}
</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active
      background #fff !important
  .wrapper
    overflow hidden
    height 100%
    height 0
    padding-bottom 30% //original 26.6%
    background #eee
    .swiper-img
      width 100%
</style>
