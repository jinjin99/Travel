<template>
  <div class="swrapper">
    <swiper :options="swiperOption" v-if="showSwiper">
      <swiper-slide v-for="item of list" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl" alt="">
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>  
</template>

<script>
export default {
  name: 'HomeSwiper',
  props:{
    list:Array 
  },
  data (){
    return {
      swiperOption: {
        pagination: ".swiper-pagination", 
        
        // 使轮播插件支持循环轮播
        loop: true
      }

    }
  },
  computed: {
    showSwiper (){
      return this.list.length
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/style/varibles.styl'
  // 由于.swiper-pagination-bullet-active 不是该组件的，要修改的话，需要这样做 
  .swrapper >>> .swiper-pagination-bullet-active
      background: white
  .swrapper
    width: 100%
    // height:31.25vw
    .swiper-img
      width: 100%
</style>