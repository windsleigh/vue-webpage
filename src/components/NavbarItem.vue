<script setup lang="ts">
import { ref, onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

const navLinksActive = ref(false);

function toggleNavLinks() {
  navLinksActive.value = !navLinksActive.value;
}

onMounted(() => {
  gsap.to(".nav", {
    scrollTrigger: {
      trigger: ".nav",
      start: "top top",
      endTrigger: "footer", // Replace with the last element on your page
      end: "bottom top",
      pin: true,
      pinSpacing: false,
    },
  });
});
</script>

<template>
  <header>
    <div class="wrapper">
      <nav class="nav">
        <RouterLink to="/" class="siteTitle">Big<b>sur</b>energy</RouterLink>
        <div class="navLinks" :class="{ active: navLinksActive }">
          <ul id="block-wrapper">
            <li class="block"><RouterLink to="/">NOSOTROS</RouterLink></li>
            <li class="block">
              <RouterLink to="/about">SERVICIOS</RouterLink>
            </li>
            <li class="block">
              <RouterLink to="/contact">CONTACTO</RouterLink>
            </li>
          </ul>
        </div>
        <div class="toggleButton" @click="toggleNavLinks">
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
        </div>
      </nav>
    </div>
  </header>
  <RouterView />
</template>

<style>
nav {
  position: sticky;
  top: 0;
  z-index: 100; /* choose an appropriate value */
  background-color: #007f80;
  color: rgb(254, 255, 205);
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 2rem;
  padding: 0 1rem;
}

.siteTitle {
  font-size: 2rem;
  margin: 0.5rem;
  text-decoration: none;
  color: inherit;
}

.navLinks ul {
  padding: 0;
  margin: 0;
  list-style: none;
  display: flex;
  gap: 1rem;
}

.navLinks a {
  color: inherit;
  font-size: 1rem;
  text-decoration: none;
  display: block;
  align-items: center;
  padding: 1rem;
}

.navLinks a:hover {
  background-color: rgb(46, 121, 121);
}

.toggleButton {
  position: absolute;
  top: 1.2rem;
  right: 1rem;
  display: none;
  flex-direction: column;
  justify-content: space-between;
  width: 30px;
  height: 21px;
}

.toggleButton .bar {
  height: 3px;
  width: 100%;
  background-color: white;
  border-radius: 10px;
}

@media (max-width: 1024px) {
  .toggleButton {
    display: flex;
  }
  .navLinks {
    display: none;
    width: 100%;
  }
  .nav {
    flex-direction: column;
    align-items: flex-start;
  }
  .navLinks ul {
    width: 100%;
    flex-direction: column;
  }
  .navLinks li {
    text-align: center;
  }
  .navLinks li {
    padding: 0.5rem 1rem;
  }
  .navLinks.active {
    display: flex;
  }
}

.siteTitle {
  font-size: 2rem;
  margin-left: 5rem;
  text-decoration: none;
  color: inherit;
}

#block-wrapper {
  width: 100%;
  margin-right: 5rem;
}
</style>
