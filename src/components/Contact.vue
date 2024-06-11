<script setup>
import { ref } from "vue";

const topics = ref([
  "general information",
  "Installing and using Debian",
  "Publicity & Press",
  "Events & Conferences",
  "Helping Debian",
  "Reporting Problems in Debian Packages",
  "Debian Development",
  "Problems with the Debian Infrastructure",
  "Harassment Issues",
]);

const isOpen = ref(false);
const topicVal = ref("topic");

</script>

<template>
  <section id="contact" class="contact mt-30 pt-30">
    <div class="container">
      <h2 class="text-transform-capitalize text-align-center">get in touch</h2>
      <form class="form mt-30">
        <div class="row">
          <div class="col-12 col-sm-6 col-md-4 p-10">
            <input type="text" placeholder="name" required />
          </div>
          <div class="col-12 col-sm-6 col-md-4 p-10">
            <input type="text" placeholder="email" required />
          </div>
          <div class="col-12 col-sm-12 col-md-4 p-10">
            <div class="topics-wrapper" :class="{ 'open': isOpen }" @click="isOpen = !isOpen">
              <p class="mb-0 text-transform-capitalize">{{ topicVal }}</p>
              <div class="options">
                <span v-for="(topic, index) in topics" :key="index" :value="topic" @click="topicVal = topic">{{ topic
                  }}</span>
              </div>
            </div>
          </div>
          <div class="col-12 p-10">
            <textarea placeholder="your message" class="mb-10" required></textarea>
          </div>
          <div class="col-12 p-10">
            <button class="main-button mx-auto">send</button>
          </div>
        </div>
      </form>
    </div>
  </section>
</template>

<style scoped lang="scss">
.contact {
  .form {

    input,
    textarea,
    .topics-wrapper {
      font-family: "Inter", sans-serif;
      width: 100%;
      background-color: transparent;
      border: 2px solid var(--border);
      color: var(--text);
      padding: 1rem;
      border-radius: 20px;
      transition: all 250ms ease-in-out;

      &::placeholder {
        text-transform: capitalize;
      }

      &:focus {
        border-color: var(--text-alt);
      }
    }

    textarea {
      min-height: 150px;
    }

    .topics-wrapper {
      position: relative;
      cursor: pointer;

      &::before {
        content: "";
        position: absolute;
        top: 50%;
        right: 1rem;
        transform: translateY(-50%) rotate(180deg);
        border: 7px solid transparent;
        border-top: 0;
        border-bottom-color: var(--text-alt);
        transition: all 250ms ease-in-out;
      }

      &.open {
        &::before {
          transform: translateY(-50%) rotate(0);
        }

        .options {
          max-height: 500px;
          border-width: 2px;
        }
      }
    }

    .options {
      position: absolute;
      top: 105%;
      left: 0;
      width: 100%;
      max-height: 0;
      display: flex;
      flex-direction: column;
      overflow: hidden;
      border: 0px solid var(--border);
      background-color: var(--background-alt);
      border-radius: 20px;
      transition: max-height 250ms ease-in-out;
      z-index: 99;

      &>* {
        color: var(--text-alt);
        text-transform: capitalize;
        padding: 1rem;
        transition: all 250ms ease-in-out;
        cursor: pointer;

        &:nth-last-child(1) {
          margin-bottom: 0;
        }

        &:hover {
          background-color: var(--main);
          color: var(--fixed);
        }
      }
    }
  }
}
</style>