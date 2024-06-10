<script setup>
import { ref } from "vue";

</script>

<template>
  <section class="about pt-30">
    <div class="container">
      <h2 class="text-align-center text-transform-capitalize mb-30">why debian</h2>
      <div class="tap-controls mx-auto">
        <button class="active">user</button>
        <button>developer</button>
        <button>enterprise</button>
      </div>
    </div>
  </section>
</template>

<style scoped lang="scss">
.about {
  .tap-controls {
    width: fit-content;
    border: 2px solid var(--border);
    border-radius: 20px;
    overflow: hidden;

    button {
      background-color: transparent;
      border: 0;
      padding: 0.8rem 1rem;
      text-transform: capitalize;
      color: var(--text);
      font-weight: 600;
      transition: all 250ms ease-in-out;

      &.active {
        background-color: var(--main);
        color: var(--fixed);
      }
    }
  }
}
</style>