<template>
  <div class="hero-image"></div>
</template>
<script>
export default {
  name: "HeroImage",
  data() {
    return {};
  }
};
</script>
<style>
.hero-image {
  position: fixed;
  min-height: 100vh;
  width: 100%;
  top: 0;
  z-index: -1;
  background-image: url("../assets/heroimage.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 80% 0;
}

.hero-image::after {
  content: "";
  background-color: rgba(0, 0, 0, 0.2);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1;
  min-height: 100vh;
}
</style>


