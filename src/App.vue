<template>
  <div class="container" :class={desktop}>
    <div class="logo"></div>
    <div class="upper">
      <a href="https://play.google.com/store/apps/details?id=com.joyours.shankm" class="google"></a>
      <a href="http://cdn.shankm.xyz/apk/GameCenter-joyoursshankm-v1.0.0-th.apk" class="android"></a>
    </div>
    <div class="middle">
      <div class="text"></div>
      <div class="layout">
        <div class="gift"></div>
        <div class="layout2">
          <div class="text2">ဂိမ္းကိုေဒါင္းလုပ္ၿပီးဘိုးနပ္လဲရမည္။</div>
          <div class="layout3">
            <div class="code">{{code}}</div>
            <div class="button" @click="handleCopyBtnClicked()">ပံုတူ</div>
          </div>
        </div>
      </div>
    </div>
    <div class="lower">
      <div class="text"></div>
      <el-carousel class="carousel" arrow="always" type="card" :height="`${carouselHeight}px`">
        <el-carousel-item v-for="item of 5" :key="item">
          <div class="item"></div>
        </el-carousel-item>
      </el-carousel>
    </div>
  </div>
</template>

<script>
import {Message} from 'element-ui'

export default {
  data() {
    return {
      code: 978238,
      carouselHeight: undefined
    }
  },
  computed: {
    desktop() {
      return !/Mobi/i.test(navigator.userAgent)
    }
  },
  methods: {
    handleCopyBtnClicked() {
      if (!navigator.clipboard) 
        return Message.warning('Browser မေထာက္ခံသျဖင့္ပံုတူမႈမေအာင္ျမင္ပါ။')
      navigator.clipboard.writeText(this.code).catch(() => Message.warning('Browser မေထာက္ခံသျဖင့္ပံုတူမႈမေအာင္ျမင္ပါ။'))
    }
  },
  mounted() {
    const containerHeight = this.$el.scrollHeight
    const carouselTop = this.$el.querySelector('.carousel').offsetTop
    this.carouselHeight = containerHeight - carouselTop - 50
  }
}
</script>

<style lang="less">
@import './styles/Normalize';

.image(@url) {
  background-image: url(@url);
  background-size: 100%;
  background-repeat: no-repeat;
}
.image(@url, @width, @height) {
  .image(@url);
  width: @width + 0px;
  height: @height + 0px;
}
.container {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #222;
  text-align: center;

  .image('./assets/bg.png');
  background-position: top;
  height: calc(100vw / 640 * 1542 * .94);
  min-height: 100vh;
  padding-top: 42.5%;
  box-sizing: border-box;
  overflow-x: hidden;

  .logo {
    position: absolute;
    top: 8px;
    left: 16px;
    @width: calc(100vw / 6);
    width: @width;
    height: calc(@width / 128 * 58);
    .image('./assets/logo.png');
  }
  .upper {
    display: flex;
    justify-content: center;

    a {
      @width: calc(100vw / 4);
      width: @width;
      height: calc(@width / 163 * 55);
      margin: 0 32px;

      &.android {.image('./assets/download-android.png');}
      &.google {.image('./assets/download-google.png');}
    }
  }
  .middle {
    .image('./assets/bg-2.png');
    @width: 100vw;
    width: @width;
    height: calc(@width / 639 * 375);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    .text {
      .image('./assets/text2.png');
      @width: 40vw;
      @height: calc(@width / 285 * 62);
      width: @width;
      height: @height;
      margin: calc(@height / 2) 0;
    }
    .layout {
      @width: 80vw;
      width: @width;
      display: flex;

      .gift {
        .image('./assets/gift.png');
        @width: 20vw;
        width: @width;
        height: calc(@width / 150 * 159);
      }
      .layout2 {
        flex: 1;

        .text2 {
          font-size: 1.6rem;
          color: #604b9f;
          height: 50%;
          display: flex;
          justify-content: center;
          align-items: center;
        }
        .layout3 {
          height: 50%;
          display: flex;
          justify-content: center;
          align-items: center;

          .code {
            flex: 1;
            height: 70%;
            background-color: #6046a5;
            color: #e2d9f8;
            border-radius: 10px;
            margin: 0 5%;
            font-size: 2.4rem;
            display: flex;
            justify-content: center;
            align-items: center;
          }
          .button {
            font-size: 1.4rem;
            color: #fff;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            width: 33%;
            height: 100%;
            .image('./assets/button.png');
            background-position: center;
          }
        }
      }
    }
  }
  .lower {
    .text {
      .image('./assets/text.png');
      @width: 80vw;
      @height: calc(@width / 461 * 61);
      width: @width;
      height: @height;
      margin: calc(@height / 2) auto;
    }
    .carousel {
      overflow-y: hidden;

      .el-carousel__item {
        &:nth-of-type(1) .item {.image('./assets/shop1.jpg');}
        &:nth-of-type(2) .item {.image('./assets/shop2.jpg');}
        &:nth-of-type(3) .item {.image('./assets/shop3.jpg');}
        &:nth-of-type(4) .item {.image('./assets/shop4.jpg');}
        &:nth-of-type(5) .item {.image('./assets/shop5.jpg');}

        .el-carousel__mask {display: none !important;}
      }
      .item {
        @width: 40vw;
        width: @width;
        height: calc(@width / 1242 * 2208);
        margin: 16px auto;
      }
    }
  }
  &.desktop {
    background-image: url('./assets/bg@HD.png');
    height: calc(100vw / 1920 * 4013 * .94);

    .logo {
      .image('./assets/logo@HD.png');
      @width: calc(100vw / 6);
      width: @width;
      height: calc(@width / 128 * 58);
    }
    .upper {
      .android {.image('./assets/download-android@HD.png');}
      .google {.image('./assets/download-google@HD.png');}
    }
    .middle {
      .image('./assets/bg-2.png');

      .text {.image('./assets/text@HD.png');}
      .layout {
        .gift {.image('./assets/gift@HD.png');}
        .layout2 {
          .text2 {font-size: 4.8rem !important;}
          .layout3 {
            .button {
              font-size: 6.5rem !important;
              .image('./assets/button@HD.png');
              }
          }
        }
      }
      .code {
        border-radius: 15px !important;
        font-size: 6.4rem !important;
      }
    }
    .lower {
      .text {.image('./assets/text2@HD.png');}
      .carousel {
        .item {
          @width: 30vw;
          width: @width;
          height: calc(@width / 1242 * 2208);
        }
      }
    }
  }
}
</style>
