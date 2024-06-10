<script setup>
import { ref } from "vue";

const images = ref([
  { path: "/src/assets/images/1und1.png", url: "http://www.1and1.info/" },
  { path: "/src/assets/images/ampere.jpg", url: "https://amperecomputing.com/" },
  { path: "/src/assets/images/bytemark_logo.svg", url: "https://www.bytemark.co.uk/r/deb-partners" },
  { path: "/src/assets/images/conova.png", url: "https://www.conova.com/" },
  { path: "/src/assets/images/credativ.png", url: "https://www.credativ.com/" },
  { path: "/src/assets/images/dgi_logo.png", url: "http://www.dg-i.net/" },
  { path: "/src/assets/images/fastly.png", url: "https://www.fastly.com/" },
  { path: "/src/assets/images/gandi.svg", url: "https://www.gandi.net/" },
  { path: "/src/assets/images/genesi-logo.png", url: "http://www.genesi-usa.com/products" },
  { path: "/src/assets/images/google.svg", url: "https://www.google.com/" },
  { path: "/src/assets/images/hetzner-logo.svg", url: "https://www.hetzner.com/" },
  { path: "/src/assets/images/hpe.png", url: "http://www.hpe.com/engage/opensource" },
  { path: "/src/assets/images/logo_eaton.png", url: "http://www.eaton.com/" },
  { path: "/src/assets/images/logo_leaseweb.png", url: "https://www.leaseweb.com/" },
  { path: "/src/assets/images/loongson.png", url: "http://www.loongson.cn/" },
  { path: "/src/assets/images/manda_logo.png", url: "http://www.man-da.de/" },
  { path: "/src/assets/images/osuosl.png", url: "http://osuosl.org/" },
  { path: "/src/assets/images/rcodezerodns.png", url: "https://www.rcodezero.at/" },
  { path: "/src/assets/images/thomas-krenn.png", url: "http://www.thomas-krenn.com/" },
  { path: "/src/assets/images/trustsec.png", url: "http://www.trustsec.de/" },
  { path: "/src/assets/images/wellcome_sanger.png", url: "https://www.sanger.ac.uk/" },
]);
</script>

<template>
  <div class="partners py-30 mt-30">
    <div class="container">
      <h2 class="mb-30 text-transform-capitalize text-align-center">our partners</h2>
      <div class="marquee">
        <div class="marquee-inner">
          <a class="mx-10 marquee-item" v-for="(image, index) in images" :key="index" :href="image.url" target="_blank">
            <img :src="image.path" />
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.partners {
  position: relative;

  &::before,
  &::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 10px;
    background: linear-gradient(to right, var(--main), transparent);
  }

  &::after {
    background: linear-gradient(to left, var(--main), transparent);
    top: auto;
    left: auto;
    bottom: 0;
    right: 0;
  }

  .marquee {
    overflow: hidden;

    .marquee-inner {
      display: flex;
      flex-wrap: nowrap;
      align-items: center;
      width: max-content;
      animation: move 15s linear infinite;

      @keyframes move {
        0% {
          transform: translateX(22%);
        }

        100% {
          transform: translateX(-100%);
        }
      }

      &:hover {
        animation-play-state: paused;
      }

      &>* {
        flex: 1 0 auto;
      }

      img {
        width: 100%;
        max-height: 200px;
      }
    }


  }
}
</style>