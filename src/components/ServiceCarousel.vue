<template>
  <div class="service-carousel-container">
    <div class="title-subtitle">
      <div class="title">SERVICIOS</div>
      <div class="subtitle">
        PARA <span class="bold">GENERACION</span> DE ENERGIA
      </div>
    </div>
    <div class="content">
      <div class="image-text-wrapper">
        <div class="image-container">
          <div class="blob"></div>
          <img
            src="@/assets/service2.png"
            alt="Service 1"
            class="service-image"
          />
        </div>
        <div class="text-block">
          <h2 class="left-aligned-title">Title</h2>
          <ul>
            <li>
              Lorem ipsum dolor sit, amet consectetur adipisicing elit. Ipsam
              quibusdam eveniet voluptate! Ipsa?
            </li>
            <li>Lorem ipsum dolor sit amet consectetur adipisicing elit.</li>
            <li>
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Magnam,
              maiores?
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ServiceCarousel",
};
</script>

<style scoped>
.service-carousel-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100%;
}

.title-subtitle {
  margin-top: 20vh;
  margin-bottom: 1em;
  align-self: flex-start;
  text-align: left;
}

.title {
  font-size: 1.5em;
  font-weight: bold;
}

.subtitle {
  font-size: 1em;
  font-style: italic;
}

.bold {
  font-weight: bold;
}

.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.image-text-wrapper {
  display: flex;
  align-items: center;
}

.image-container,
.text-block {
  width: 30vw;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: visible;
}

.blob {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  background-image: url("@/assets/blob.png");
  background-size: contain; /* Or you can use 'cover' based on what suits your design */
  background-position: center;
  background-repeat: no-repeat;
  z-index: -1;
  transition: all 1s ease;
}

.service-image {
  max-width: 80%;
  position: relative;
  z-index: 1;
  transition: all 1s ease;
}

.image-container:hover .blob {
  transform: translateX(-20px);
}

.image-container:hover .service-image {
  transform: translateX(20px);
}

.text-block {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

.left-aligned-title {
  text-align: left;
  align-self: flex-start;
  width: 100%;
}
</style>
