<template>
  <div class="cardBody">
    <Swiper
      :effect="'coverflow'"
      :grabCursor="true"
      :centeredSlides="true"
      :slidesPerView="'auto'"
      :coverflowEffect="{
        rotate: 0,
        stretch: 0,
        depth: 100,
        modifier: 4,
        slideShadows: false,
      }"
      :loop="true"
      :pagination="false"
      :modules="modules"
      class="swiper-container"
    >
      <SwiperSlide class="swiper-slide" v-for="(hero, index) in heroData" :key="index" :style="{'--heroColor' : hero.color}">
        <div class="content">
          <h2>{{ hero.name }}</h2>
          <p>{{ hero.desc }}</p>
          <a href="#"> Read More </a>
        </div>
        <img :src="heroCharacterData[index]" alt="" />
      </SwiperSlide>
    </Swiper>
  </div>
</template>

<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/effect-coverflow";
import "swiper/css/pagination";
import { EffectCoverflow, Pagination } from "swiper/modules";

import heroData from "../data/Marvel.json";

import CaptainMarvel from "../assets/img.png";
import CaptainAmerican from "../assets/american-captain.png";
import IronMan from "../assets/iron-man.png";
import SpiderMan from "../assets/spider-man.png";
import Hulk from "../assets/Hulk.png";
import Hawkeye from "../assets/hawkeye.png";
import blackPanther from "../assets/black-panther.png";
import BlackWidow from "../assets/black-widow.png";
import DoctorStrange from "../assets/doctor-strange.png";
import AntMan from "../assets/ant-man.png";
import Deadpool from "../assets/deadpool.png";

export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      heroData: heroData,
      heroCharacterData: [CaptainMarvel, SpiderMan, IronMan, CaptainAmerican, Hulk, BlackWidow, Hawkeye, blackPanther, DoctorStrange, AntMan, Deadpool]
    };
  },
  setup() {
    return {
      modules: [EffectCoverflow, Pagination],
    };
  },
};

</script>

<style scoped>
.cardBody {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100vh;
  overflow: hidden;
  z-index: 9999;
}

.swiper-container {
  width: 100%;
  margin-top: -400px;
  padding-top: 200px;
  padding-bottom: 200px;
}

.swiper-slide {
  position: relative;
  width: 600px;
  height: 350px;
  margin: 20px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  border-radius: 20px;
  background-position: center;
  background-size: cover;
  box-shadow: 0 15px 50px rgba(0, 0, 0, 0.2);
  filter: blur(6px) brightness(0.5);
  background: var(--heroColor);
  transition: 1s;
  z-index: 99999;
}

.swiper-slide-active {
  filter: blur(0px) brightness(1);
}

.swiper-slide-active::before {
  content: "";
  position: absolute;
  top: 20%;
  left: 50%;
  transform: translateX(-50%);
  width: 90%;
  height: 83%;
  opacity: 0;
  visibility: hidden;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  border-radius: 20px;
  filter: blur(0px);
  z-index: -99;
  transition: 0.5s;
  background: var(--heroColor);
}

.swiper-slide-active:hover::before {
  content: "";
  position: absolute;
  opacity: 1;
  visibility: visible;
  filter: blur(30px);
  z-index: -99;
}

.swiper-slide img {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  height: 400px;
  transition: 0.5s;
}

.swiper-slide-active:hover img {
  left: 80%;
  height: 500px;
}

.swiper-slide .content {
  position: relative;
  width: 40%;
  left: 20%;
  padding: 0px 20px 20px 30px;
  opacity: 0;
  visibility: hidden;
  transition: 0.5s;
}

.swiper-slide-active:hover .content {
  left: 0%;
  opacity: 1;
  visibility: visible;
}

.swiper-slide .content h2 {
  color: #fff;
  text-transform: uppercase;
  font-size: 2em;
  line-height: 1em;
}

.swiper-slide .content p {
  font-size: 0.9em;
  color: #fff;
}

.swiper-slide .content a {
  position: relative;
  display: inline-block;
  color: #111;
  padding: 10px 20px;
  border-radius: 10px;
  background: #fff;
  margin-top: 10px;
  text-decoration: none;
}

@media (max-width: 991px) {
  .swiper-slide {
    position: relative;
    width: auto;
    max-width: 600px;
    align-items: flex-start;
  }
  .swiper-slide-active {
    transition: all 0.5s ease-in-out 0s !important;
  }

  /* .swiper-slide-active:hover::before {
    content: "";
    position: absolute;
    opacity: 1;
    visibility: visible;
    max-width: 620px;
    height: 620px;
    left: -10px;
  } */
  .swiper-slide-active:hover {
    height: 650px;
  }

  .swiper-slide-active:hover img {
    left: 50%;
    height: 350px;
  }

  .swiper-slide .content p {
    color: #fff;
    text-align: justify;
    /* margin-right: 30px; */
  }

  .swiper-slide .content {
    position: relative;
    width: 100%;
    left: 0;
    padding: 0px 60px;
  }

  @media (max-width: 650px) {
    /* .swiper-slide-active:hover::before {
      opacity: 0;
      visibility: hidden;
    } */

    .swiper-slide {
      max-width: 300px;
    }
  }

  @media (max-width: 421px) {
    .swiper-container{
      margin-top: 0;
    }
    .swiper-slide .content {
      padding: 0 30px;
    }

    .swiper-slide-active:hover img {
      left: 50%;
      height: 300px;
    }

    .swiper-slide .content h2 {
      color: #fff;
      text-transform: uppercase;
      font-size: 2em;
      line-height: 1em;
    }

    .swiper-slide .content p {
      font-size: 14px;
    }

    .swiper-slide-active:hover {
      height: 600px;
    }
  }
}
</style>
