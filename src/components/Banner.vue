<script>
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";

import "swiper/css/pagination";

// import './style.css';

// import required modules
import { Pagination } from "swiper/modules";
import axios from "axios";

export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      bannerList: [],
    };
  },
  setup() {
    async function getBannerListing() {
      await axios.get("https://api.npoint.io/fee177346e7875554413").then((res) => {
        this.bannerList = res.data.slides;
      });
    }
    function ImgNotLoaded(e) {
      e.target.src = "../assets/images/bannerImg.jpg";
    }
    return {
      modules: [Pagination],
      getBannerListing,
      ImgNotLoaded,
    };
  },
  mounted() {
    this.getBannerListing();
  },
};
</script>

<template>
  <div class="container">
    <swiper :pagination="true" :modules="modules" class="mySwiper banner">
      <swiper-slide
        v-for="item in bannerList"
        :key="item.id"
        :style="{ display: `flex`, order: item.order }"
      >
        <div class="banner__aspect-ratio">
          <!--on error should be used as the img urls are empty-->
          <img src="../assets/images/bannerImg.jpg" alt="banner-img" />
        </div>
        <div class="banner__body" :style="{ order: item.order }">
          <h5 class="banner__body__category">{{ item.category }}</h5>
          <h1 class="banner__body__main-title">
            {{ item.title }}
          </h1>
          <p class="banner__body__brief">{{ item.brief }}</p>
          <div class="banner__body__actions">
            <a
              class="banner__body__actions--details generic-orange-btn"
              href="https://www.youtube.com/"
              target="_blank"
              >Find out more</a
            >
            <button class="banner__body__actions--video">
              <img src="../assets/images/play-button.png" />
              Play Demo
            </button>
          </div>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<style lang="scss">
.banner {
  .banner__aspect-ratio {
    position: relative;
    max-width: 100%;
    height: auto;
    display: contents;
    &::before {
      display: block;
      content: "";
      width: 100%;
      padding-top: calc((73 / 130) * 100%);
    }
    img {
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      max-width: 100%;
    }
  }
  .banner__body {
    position: absolute;
    top: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    height: 100%;
    max-width: 50%;
    .banner__body__category {
      color: var(--pink-color);
      font-family: "poppins-bold";
      margin-bottom: 30px;
    }
    .banner__body__main-title {
      font-family: sans-serif;
      font-weight: bold;
      color: #181e4b;
      margin-bottom: 24px;
      font-size: calc(65px + (45 - 65) * ((100vw - 1366px) / (1920 - 1366)));
    }
    .banner__body__brief {
      font-family: "poppins-medium";
      color: var(--txt-color);
      margin-bottom: 35px;
    }
    .banner__body__actions {
      .banner__body__actions--details {
        &.generic-orange-btn {
          display: inline-block;
          background-color: var(--orange-color);
          color: var(--vt-c-white);
          padding: 15px 20px;
          border-radius: 5px;
          margin-inline-end: 45px;
        }
      }
      .banner__body__actions--video {
        border: none;
        background-color: transparent;
        padding: 5px;
        font-weight: 500;
        color: var(--txt-color);
        img {
          width: 45px;
          margin-inline-end: 15px;
        }
      }
    }
  }
  @media (max-width: 768px) {
    .banner__body {
      .banner__body__category {
        margin-bottom: 10px;
      }
      .banner__body__main-title {
        font-size: calc(14px + (12 - 14) * ((100vw - 768px) / (1024 - 768)));
        margin-bottom: 10px;
      }
      .banner__body__brief {
        font-size: calc(14px + (11 - 14) * ((100vw - 768px) / (1024 - 768)));
        margin-bottom: 10px;
      }
      .banner__body__actions {
        .banner__body__actions--details {
          &.generic-orange-btn {
            padding: 10px;
          }
        }
      }
    }
  }
  @media (max-width: 767px) {
    .banner__aspect-ratio {
      &::before {
        padding-top: 75.153846%;
      }
    }
    .banner__body {
      max-width: 100%;
      .banner__body__category,
      .banner__body__brief {
        //we can use also clamp for fontsize it's build on top of fluid typography
        font-size: calc(14px + (12 - 14) * ((100vw - 320px) / (767 - 320)));
      }
      .banner__body__main-title {
        font-size: calc(18px + (16 - 18) * ((100vw - 320px) / (767 - 320)));
      }
      .banner__body__actions {
        .banner__body__actions--details {
          &.generic-orange-btn {
            margin-inline-end: 25px;
          }
        }
        .banner__body__actions--video {
          img {
            width: 35px;
          }
          color: var(--vt-c-white);
        }
      }
    }
  }
}
.swiper {
  .swiper-pagination {
    text-align: unset;
    margin-inline-start: 10px;
    bottom: 15px;
    .swiper-pagination-bullet {
      width: 30px;
      height: 30px;
      margin-inline-end: 75px;
      position: relative;
      &:first-child {
        background: var(--pink-color);
      }
      &:nth-child(2) {
        background: var(--green-color);
      }
      &:nth-child(3) {
        background: var(--orange-color);
        &::after {
          display: none;
        }
      }
      &::after {
        content: " . . . . . . . ";
        position: absolute;
        right: -70px;
        bottom: 8px;
        font-weight: bold;
        color: #959292;
      }
    }
    .swiper-pagination-bullet {
      &.swiper-pagination-bullet-active {
        margin-inline-end: 90px;
        width: 35px;
        height: 35px;
        &:first-child {
          background: var(--pink-color);
        }
        &:nth-child(2) {
          background: var(--green-color);
        }
        &:nth-child(3) {
          background: var(--orange-color);
        }
      }
    }

    @media (max-width: 767px) {
      bottom: 0;
      margin: 0;
      margin-inline-start: 0;
      text-align: center;
      .swiper-pagination-bullet {
        width: 20px;
        height: 20px;
        left: 25px;
        &::after {
          bottom: 4px;
        }
      }
      .swiper-pagination-bullet {
        &.swiper-pagination-bullet-active {
          width: 25px;
          height: 25px;
        }
      }
    }
  }
}
</style>
