<template lang="html">
  <div class="silder">
    <swiper :options="swiperOption">
      <swiper-slide>
        <img src="../assets/banner/b1.jpg" alt="">
      </swiper-slide>
      <swiper-slide>
        <img src="../assets/banner/b2.jpg" alt="">
      </swiper-slide>
      <swiper-slide>
        <img src="../assets/banner/b3.jpg" alt="">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
      
    </swiper>
  </div>
</template>

<script>
export default {
  name:"slider",
  data(){
    return{
      swiperOption: {
        pagination: {
          el: '.swiper-pagination',
        },
        loop:true,
        autoplay : 1000,
        observer:true,//修改swiper自己或子元素时，自动初始化swiper 
        observeParents:false,//修改swiper的父元素时，自动初始化swiper 
//         onSlideChangeEnd: function(swiper){ 
// 　　　   swiper.update();  
// 　　　   mySwiper.startAutoplay();
// 　　     mySwiper.reLoop();
//         }
      }
    }
  }
}
</script>

<style scoped>

</style>
