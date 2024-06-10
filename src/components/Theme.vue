<script setup>
import { Icon } from '@iconify/vue';
import { ref, onMounted } from 'vue';

const theme = ref("light");

const applyDark = () => {
  document.documentElement.classList.add("dark");
  localStorage.setItem("theme", "dark");
  theme.value = "dark";
}

const applyLight = () => {
  document.documentElement.classList.remove("dark");
  localStorage.setItem("theme", "light");
  theme.value = "light";
}

onMounted(() => {
  if (localStorage.getItem("theme")) {
    localStorage.getItem("theme") === "dark" ? applyDark() : applyLight();
  } else {
    (window.matchMedia("(prefers-color-scheme: dark)").matches === true) ? applyDark() : applyLight();
  }
});

const toggleTheme = () => {
  localStorage.getItem("theme") === "dark" ? applyLight() : applyDark();
}

</script>

<template>
  <button @click="toggleTheme" class="theme-button">
    <Icon icon="ph:sun-bold" v-if="theme === 'dark'" />
    <Icon icon="solar:moon-bold" v-else />
  </button>
</template>

<style scoped lang="scss">
.theme-button {
  cursor: pointer;
  font-size: 1.1rem;
  background-color: transparent;
  border: 0;
  color: var(--text);
}
</style>