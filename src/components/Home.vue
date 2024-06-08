<script setup>
import { Icon } from '@iconify/vue';
</script>

<template>
  <section class="home d-flex align-items-center">
    <div class="container">
      <div class="row">
        <div class="col-12 col-lg-6 align-self-center order-2 order-lg-1">
          <div class="content-wrapper">
            <h1 class="mb-25 text-transform-capitalize text-align-center lg-text-align-left"><span
                class="text-transform-uppercase">debian</span> the
              universal &
              complete free operating system</h1>
            <div class="text-align-center lg-text-align-left">
              <a href="#" class="main-button">
                <Icon icon="material-symbols:download" />
                <span class="px-3">download</span>
              </a>
              <a href="#" class="sec-button ml-10">
                <Icon icon="material-symbols:layers" />
                <span class="px-3">flavors</span>
              </a>
            </div>
          </div>
        </div>
        <div class="col-12 col-lg-6 order-1 order-lg-2">
          <div class="image-wrapper mb-25 lg-mb-0">
            <img src="/debian.svg" class="mx-auto" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped lang="scss">
.home {
  .content-wrapper {
    position: relative;

    &::before {
      content: "";
      position: absolute;
      top: -40%;
      left: -40%;
      width: 60%;
      height: 100%;
      background-color: var(--main);
      border-radius: 50%;
      opacity: 0.3;
      filter: blur(100px);
      z-index: -1;
    }

    h1 {
      span {
        background: linear-gradient(to right, var(--main), var(--main-mono));
        background-clip: text;
        -webkit-text-fill-color: transparent;
      }
    }
  }

  .image-wrapper {
    width: 100%;

    img {
      width: 400px;

      @media (max-width: 991px) {
        width: 200px;
      }
    }
  }
}
</style>