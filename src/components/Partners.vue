<script setup>
import { ref } from "vue";

const images = ref([
  { path: "/images/1und1.png", url: "http://www.1and1.info/" },
  { path: "/images/ampere.jpg", url: "https://amperecomputing.com/" },
  { path: "/images/bytemark_logo.svg", url: "https://www.bytemark.co.uk/r/deb-partners" },
  { path: "/images/conova.png", url: "https://www.conova.com/" },
  { path: "/images/credativ.png", url: "https://www.credativ.com/" },
  { path: "/images/dgi_logo.png", url: "http://www.dg-i.net/" },
  { path: "/images/fastly.png", url: "https://www.fastly.com/" },
  { path: "/images/gandi.svg", url: "https://www.gandi.net/" },
  { path: "/images/genesi-logo.png", url: "http://www.genesi-usa.com/products" },
  { path: "/images/google.svg", url: "https://www.google.com/" },
  { path: "/images/hetzner-logo.svg", url: "https://www.hetzner.com/" },
  { path: "/images/hpe.png", url: "http://www.hpe.com/engage/opensource" },
  { path: "/images/logo_eaton.png", url: "http://www.eaton.com/" },
  { path: "/images/logo_leaseweb.png", url: "https://www.leaseweb.com/" },
  { path: "/images/loongson.png", url: "http://www.loongson.cn/" },
  { path: "/images/manda_logo.png", url: "http://www.man-da.de/" },
  { path: "/images/osuosl.png", url: "http://osuosl.org/" },
  { path: "/images/rcodezerodns.png", url: "https://www.rcodezero.at/" },
  { path: "/images/thomas-krenn.png", url: "http://www.thomas-krenn.com/" },
  { path: "/images/trustsec.png", url: "http://www.trustsec.de/" },
  { path: "/images/wellcome_sanger.png", url: "https://www.sanger.ac.uk/" },
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