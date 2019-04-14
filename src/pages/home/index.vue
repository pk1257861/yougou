<template>
  <div>
    <!-- 搜索 -->
    <div class="search">
      <div class="serach_input">
        <input type="text">
        <div class="word">
          <icon type="search" size="20"></icon>
          <span>搜索</span>
        </div>
      </div>
    </div>
    <!-- 轮播图  -->
    <swiper class="loop" circular indicator-dots autoplay>
      <block v-for="(item,index) in imgList" :key="index">
        <swiper-item>
          <image :src="item.image_src" />>
        </swiper-item>
      </block>
    </swiper>
  </div>
</template>

<script>
export default {   
 data() {
   return {
     imgList:[],
     a:1
   }
 },
 mounted() {
  wx.request({
     url:"https://itjustfun.cn/api/public/v1/home/swiperdata",
     data: { },
  header: {
    'content-type': 'application/json' // 默认值
  },
  success: (res)=>{
   
   this.imgList=res.data.data
    console.log(res)
  }
   })
 },
};
</script>

<style lang=less>
@import "./index.less";
</style>
