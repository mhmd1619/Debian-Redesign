<script setup>
import { Icon } from '@iconify/vue';
import { onMounted, ref } from "vue";
import Theme from "./Theme.vue";

const isScroll = ref(false);
const isCollapsed = ref(true);

const handleScroll = () => {
  (window.scrollY > 5) ? isScroll.value = true : isScroll.value = false;
}
onMounted(() => {
  onscroll = () => handleScroll();
})
</script>

<template>
  <nav :class="{ 'scrolled': isScroll }">
    <div class="container d-flex justify-content-space-between align-items-center flex-wrap-wrap">
      <a href="/" class="logo">
        <img src="/debian.svg" />
      </a>
      <button class="menu d-flex align-items-center justify-content-center d-lg-none"
        @click="isCollapsed = !isCollapsed">
        <Icon icon="material-symbols:menu" />
      </button>
      <div class="links-wrapper" :class="{ 'collapsed': isCollapsed }">
        <a href="#" class="link" @click="isCollapsed = !isCollapsed">download</a>
        <a href="#about" class="link" @click="isCollapsed = !isCollapsed">about</a>
        <a href="#news" class="link" @click="isCollapsed = !isCollapsed">news</a>
        <a href="#contact" class="link" @click="isCollapsed = !isCollapsed">contact us</a>
        <a class="link" @click="isCollapsed = !isCollapsed">
          <Theme />
        </a>
      </div>
    </div>
  </nav>
</template>

<style scoped lang="scss">
nav {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  padding: 0.5rem 0;
  z-index: 9999;
  transition: all 250ms ease-in-out;

  &.scrolled {
    background-color: var(--background-alt);
    border-bottom: 2px solid var(--border);
  }

  .logo {
    img {
      width: 50px;
    }
  }

  .menu {
    background: transparent;
    width: 50px;
    height: 40px;
    border: 0;
    font-size: 32px;
    color: var(--text);
  }

  .links-wrapper {
    display: flex;
    align-items: center;


    .link {
      text-transform: capitalize;
      padding: 0 0.5rem;
      font-weight: 500;
    }

    @media (max-width: 991px) {
      flex-direction: column;
      flex: 1 0 100%;
      align-items: start;
      padding-top: 1rem;
      background-color: var(--background-alt);
      overflow: hidden;
      max-height: 300px;
      transition: all 250ms linear;

      &.collapsed {
        max-height: 0;
        padding: 0;
      }

      .link {
        padding: 0.5rem;
      }
    }

  }
}
</style>