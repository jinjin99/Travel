<template>
  <div>
    <router-link class="header-abs" to="/" tag="div" v-show="showAbs"> 
      <div class="iconfont header-abs-back">&#xe624;</div>
    </router-link>
    <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
      <router-link to="/"> 
       <div class="iconfont header-fixed-back">&#xe624;</div>
      </router-link>
      景点详情
    </div>
  </div>
</template>

<script>
export default {
  name:'DetailHeader',
  data (){
    return{
      showAbs:true,
      opacityStyle:{
        opacity: 0
      }
    }
  },
  methods:{
    handleScroll(){
      const top = document.documentElement.scrollTop
      if(top>60 )
      {
      let opacity = top/140
      opacity = opacity>1? 1: opacity
      this.opacityStyle = {
        opacity
      }
     this.showAbs = false
      
      }
     else{
        this.showAbs = true
      }
    }
  },
  activated (){
    window.addEventListener('scroll',this.handleScroll)
  },
  // 在页面即将被隐藏，或者即将被替换成别的页面时，执行这个函数。
  deactivated(){
    window.removeEventListener('scroll',this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~@/assets/style/varibles.styl'
  .content
    height: 50rem
  .header-abs
    position:absolute
    left: .2rem
    top: .2rem
    width: .8rem
    height: .8rem
    line-height: .8rem
    text-align: center
    border-radius: .4rem
    background: rgba(0,0,0,.8)
    .header-abs-back
      color:#fff
      font-size:.32rem
  .header-fixed
    position: fixed
    top:0
    right:0
    left:0
    overflow: hidden
    height: .86rem
    line-height: .86rem
    text-align: center
    color: #fff
    z-index: 99
    background: $bgColor
    font-size: .32rem
    .header-fixed-back
      position: absolute
      top: 0
      left: 0
      width: .64rem
      text-align: center
      font-size: .4rem
      color: #fff
</style>