<template>
    <section  class="child-container">
      <swiper
        :indicator-dots="indicatorDots"
        :indicator-color="indicatorColor"
        :indicator-active-color="indicatorActiveColor"
        :current="current"
        :autoplay="autoplay"
        :interval="interval"
        :duration="duration"
        :circular="circular"
        :vertical="vertical"
        :display-multiple-items="displayMultipleItems"
        :previous-margin="previousMargin"
        :next-margin="nextMargin"
      >
        <block>
          <swiper-item v-for="(item,i) in imgUrls" :key="i" :item-id="i">
            <image mode="widthFix" :src="item" @click.stop="handlePreviewImg(i)"/>
          </swiper-item>
        </block>
      </swiper>
      <p class="haibao-img-p">点击海报 - 长按海报 - 发送给朋友</p><div>
      </div>
    </section>
</template>

<script>
  export default {
    name: 'YqylLunboImages',
    props: {
      // 设置高度
      swiperH: {
        type: String,
        default: '340rpx'
      },
      // 数据数组
      imgArr: {
        type: Array,
        required: true
      }
    },
    data () {
      return {
        // 设置swiper的高度
        swiperHeight: this.swiperH,
        // imgUrls: this.imgArr,
        imgUrls: this.imgArr,
        // 是否显示指示点
        indicatorDots: true,
        // 指示点颜色
        indicatorColor: '#ccc',
        // 活动的指示点颜色
        indicatorActiveColor: '#fff',
        // 当前所在滑块
        current: 0,
        // 是否自动播放
        autoplay: false,
        // 切换间隔时间
        interval: 5000,
        // 滑动动画时长
        duration: 500,
        // 是否采用衔接滑动
        circular: false,
        // 滑动方向是否为纵向
        vertical: false,
        // 同时显示的滑块数量
        displayMultipleItems: 1,
        // 前边距，可露出前一项的一小部分，px或rpx
        previousMargin: '-1rpx',
        // 后边距，可露出后一项的一小部分，px或rpx
        nextMargin: '-1rpx'
      }
    },
    methods: {
      handlePreviewImg (i) {
        this.current = i;
        mpvue.previewImage({
          urls: this.imgUrls,
          current: this.imgUrls[i]
        })
      }
    },
    watch: {
      imgArr: function (val) {
        this.imgUrls = val;
      }
    },
    created () {
    }
  }
</script>

<style scoped lang="scss">
  .child-container{
    height: 100%;
    width: 100%;
    background: rgba(0,0,0,.5);
    position: fixed;
    left: 0rpx;
    top: 0rpx;
    z-index: 1000;
    swiper{
      margin:8% auto;
      height: 85%;
      width: 86%;
      swiper-item{
        height: auto;
        -webkit-border-radius: 12rpx;
        -moz-border-radius: 12rpx;
        border-radius: 12rpx;
        /*border: 1px solid red;*/
        image{
          width: 90%;
          max-height: 100%;
          margin-left: 5%;
          background: url("../../../static/images/BannerNull.png");
          background-size: 100% 100%;
          -webkit-border-radius: 12rpx;
          -moz-border-radius: 12rpx;
          border-radius: 12rpx;
        }
      }
    }
    .haibao-img-p{
      position: absolute;
      left: 0rpx;
      bottom: 3%;
      width: 100%;
      text-align: center;
      color: #FFFFFF;
      font-size: 30rpx;
      letter-spacing: 4rpx;
    }
  }
</style>
