<script setup>

</script>

<template>
  <footer class="mt-30 py-20">
    <div class="links d-flex justify-content-center mb-20">
      <a href="#">download</a>
      <a href="#">about</a>
      <a href="#">news</a>
      <a href="#">contact us</a>
    </div>
    <div class="text-align-center">
      <h4 class="text-transform-capitalize">Copyright © 1997-2024 SPI and others; See license terms</h4>
      <h4 class="text-transform-capitalize">Debian is a registered trademark of Software in the Public Interest, Inc.
      </h4>
    </div>
  </footer>
</template>

<style scoped lang="scss">
footer {
  background: radial-gradient(var(--main-mono), var(--main));
  color: var(--fixed);

  .links {
    a {
      text-decoration: underline;
      text-transform: capitalize;
      padding: 0.5rem;
    }
  }
}
</style>