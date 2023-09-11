<!-- src/views/HomeView.vue -->
<template>
  <div class="home-container">
    <div class="message-container">
      <div class="title-element" ref="titleElement">
        <div class="line"></div>
        <div class="text-container">
          <div class="light-text larger-font italic-text">OPTIMIZAMOS</div>
          <div class="bold-text larger-font italic-text">TU ENERGÍA</div>
        </div>
      </div>
    </div>
  </div>
  <div class="crane-container">
    <div class="crane-text">
      Nuestro enfoque principal está en apoyar a nuestros clientes en todo lo
      relacionado con energía, para ayudarlo a obtener beneficios adicionales
      sin tener que desviar recursos de su Core Business.
    </div>
    <img src="@/assets/crane.jpg" alt="Crane" class="crane-image" />
  </div>
  <div class="lighter-teal-block">
    <div class="carousel-wrapper">
      <ServiceCarousel />
    </div>
  </div>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import ServiceCarousel from "@/components/ServiceCarousel.vue";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "HomeView",
  components: {
    ServiceCarousel,
  },
  mounted() {
    this.homePageAnimation();
    this.setupCraneScrollAnimation();
  },
  methods: {
    homePageAnimation() {
      const tl = gsap.timeline();

      tl.from(this.$refs.titleElement, {
        duration: 1,
        x: -100,
        opacity: 0,
        ease: "power2.out",
      });
    },
    setupCraneScrollAnimation() {
      gsap.to(".crane-image", {
        yPercent: -30,
        ease: "none",
        scrollTrigger: {
          trigger: ".crane-container",
          start: "top bottom",
          end: "bottom top",
          scrub: true,
        },
      });
    },
  },
};
</script>

<style scoped>
.home-container {
  background-image: url("@/assets/wind.jpg");
  background-size: cover;
  background-position: center;
  height: 100vh;
  display: flex;
  justify-content: flex-end; /* Aligns children to the right */
  align-items: center;
}

.message-container {
  text-align: center;
  display: flex;
  align-items: center;
  margin-right: 20%; /* Adds right margin */
}

.title-element {
  display: flex;
  align-items: center;
}

.line {
  width: 2px;
  height: 70px; /* Adjusted from 40px to 60px to make the line longer */
  background-color: #000000;
  margin-right: 20px;
  transform: rotate(10deg);
}

.text-container {
  text-align: left;
}

.bold-text,
.light-text {
  font-size: 2em;
}

.light-text {
  font-weight: 300;
}

.bold-text {
  font-weight: bold;
}

.italic-text {
  font-style: italic;
}

.crane-container {
  position: relative;
  overflow: hidden;
  height: 40vh; /* or however tall you want the visible area to be */
  position: relative;
}

.crane-container::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 97, 76, 0.637); /* Teal color with 50% opacity */
  z-index: 2;
}
.crane-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: auto;
  z-index: 1;
  transform: scale(1.8); /* Zooms in the image by 20% */
  z-index: 1;
}
.crane-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 3;
  color: #eeeeee; /* Choose the text color you prefer */
  text-align: center;
  max-width: 50%; /* Or whatever maximum width you want */
  font-size: 1.5em;
}

.lighter-teal-block {
  background-color: rgba(0, 197, 99, 0.473); /* Lighter teal with 20% opacity */
  height: 100vh; /* 50% of the viewport height */
  display: flex; /* Using Flexbox to center the content */
  justify-content: center; /* Horizontal Centering */
  align-items: center; /* Vertical Centering */
}

.carousel-wrapper {
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
