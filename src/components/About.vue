<script setup>
import { Icon } from '@iconify/vue';
import { ref } from "vue";

const isCategory = ref("user");

const buttons = ref([
  { text: "user", isActive: true },
  { text: "developer", isActive: false },
  { text: "enterprise", isActive: false },
]);

const handleControls = (index) => {
  buttons.value.forEach(button => {
    button.isActive = false;
  });
  buttons.value[index].isActive = true;
  isCategory.value = buttons.value[index].text;
}

const features = ref([
  { category: "user", icon: "pepicons-pop:dollar-off", title: "debian is free", info: "Debian is made of free and open source software and will always be 100% free. Free for anyone to use, modify, and distribute. This is our main promise to our users. It's also free of cost." },
  { category: "user", icon: "tdesign:secured", title: "Debian is stable and secure", info: "Debian is a Linux-based operating system for a wide range of devices including laptops, desktops and servers. We provide a reasonable default configuration for every package as well as regular security updates during the packages' lifetimes." },
  { category: "user", icon: "ion:hardware-chip-outline", title: "Debian has extensive Hardware Support", info: "Most hardware is supported by the Linux kernel which means that Debian will support it as well. Proprietary drivers for hardware are available if necessary." },
  { category: "user", icon: "hugeicons:check-list", title: "Debian offers a flexible Installer", info: "Our Live CD is for everyone who wants to give Debian a try before installing it. It also includes the Calamares installer which makes it easy to install Debian from the live system. More experienced users can use the Debian installer with more options for fine-tuning, including the possibility to use an automated network installation tool." },
  { category: "user", icon: "material-symbols:update", title: "Debian provides smooth Upgrades", info: "It's easy to keep our operating system up-to-date, whether you want to upgrade to a completely new release or just update a single package." },
  { category: "user", icon: "ic:baseline-assistant", title: "Debian is the Base for many other Distributions", info: "Everyone can be a part of our community; you don't have to be a developer or sysadmin. Debian has a democratic governance structure. Since all members of the Debian project have equal rights, Debian cannot be controlled by a single company. Our developers are from more than 60 different countries, and Debian itself is translated into more than 80 languages." },
  { category: "user", icon: "iconoir:community", title: "The Debian Project is a Community", info: "Everyone can be a part of our community; you don't have to be a developer or sysadmin. Debian has a democratic governance structure. Since all members of the Debian project have equal rights, Debian cannot be controlled by a single company. Our developers are from more than 60 different countries, and Debian itself is translated into more than 80 languages." },
  { category: "developer", icon: "material-symbols:architecture", title: "Multiple Hardware Architectures", info: "Debian supports a long list of CPU architectures, including amd64, i386, multiple versions of ARM and MIPS, POWER7, POWER8, IBM System z and RISC-V. Debian is also available for niche architectures." },
  { category: "developer", icon: "fluent:iot-16-filled", title: "IoT and Embedded Devices", info: "Debian runs on a wide range of devices, like the Raspberry Pi, variants of QNAP, mobile devices, home routers and a lot of Single Board Computers (SBC)." },
  { category: "developer", icon: "eos-icons:software", title: "Huge Number of Software Packages", info: "Debian has a large number of packages (currently in stable: 59000 packages) which use the deb format." },
  { category: "developer", icon: "material-symbols:new-releases", title: "Different Releases", info: "Besides our stable release, you can install newer software versions by using the testing or unstable releases." },
  { category: "developer", icon: "fa-solid:bug", title: "Public Bug Tracker", info: "Our Debian bug tracking system (BTS) is publicly available for everybody via a web browser. We do not hide our software bugs, and you can easily submit new bug reports or join the discussion." },
  { category: "developer", icon: "mdi:tools", title: "Debian Policy and Developer Tools", info: "Debian offers high-quality software. To learn more about our standards, read the policy which defines technical requirements for every package included in the distribution. Our Continuous Integration strategy involves Autopkgtest (runs tests on packages), Piuparts (tests installation, upgrade and removal), and Lintian (checks packages for inconsistencies and errors)." },
  { category: "enterprise", icon: "solar:like-bold", title: "Debian is reliable", info: "Debian proves its reliability every day in thousands of real world scenarios, ranging from single user laptops to super-colliders, stock exchanges and the automotive industry. It's also popular in the academic world, in science and in the public sector." },
  { category: "enterprise", icon: "grommet-icons:user-expert", title: "Debian has many Experts", info: "Our package maintainers do not only take care of the Debian packaging and incorporating new upstream versions. Often they're experts on the application itself and therefore contribute to upstream development directly." },
  { category: "enterprise", icon: "tdesign:secured", title: "Debian is secure", info: "Debian offers security support for its stable releases. Many other distributions and security researchers rely on Debian's security tracker." },
  { category: "enterprise", icon: "material-symbols:support", title: "Long Term Support", info: "Debian's free of charge Long Term Support (LTS) version extends the lifetime of all Debian stable releases to at least 5 years. Additionally, the commercial Extended LTS initiative supports a limited set of packages for more than 5 years." },
  { category: "enterprise", icon: "ic:baseline-cloud-done", title: "Cloud Images", info: "Official cloud images are available for all major cloud platforms. We also provide the tools and configuration so you can build your own customized cloud images. You can also use Debian in virtual machines on the desktop or in a container." },
])

</script>

<template>
  <section id="about" class="about pt-30">
    <div class="container">
      <h2 class="text-align-center text-transform-capitalize mb-30">why debian</h2>
      <div class="tap-controls mx-auto">
        <button v-for="(button, index) in buttons" :key="index" :class="{ 'active': button.isActive }"
          @click="handleControls(index)">{{ button.text }}</button>
      </div>
      <div class="grid mt-30">
        <div class="" v-for="(feature, index) in features.filter(e => e.category === isCategory)" :key="index">
          <div class="box text-align-center">
            <span class="icon">
              <Icon :icon=feature.icon />
            </span>
            <h4 class="title">{{ feature.title }}</h4>
            <p>{{ feature.info }}</p>
          </div>
        </div>
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

  .grid {
    counter-reset: grid;
    columns: 18rem;
    gap: 2rem;
  }

  .box {
    border: 2px solid var(--border);
    border-radius: 20px;
    padding: 1.5rem;
    break-inside: avoid;
    margin-bottom: 2rem;
    transition: all 250ms ease-in-out;

    &:hover {
      box-shadow: 0 0 20px var(--border);
    }

    .icon {
      color: var(--main);
      font-size: 4rem;
    }

    .title {
      text-transform: capitalize;
    }
  }
}
</style>