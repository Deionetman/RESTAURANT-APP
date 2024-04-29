<script setup>
defineProps(["headerTitle", "aboutUsText", "buttonText"]);
</script>

<template>
  <div>
    <div class="container">
      <div class="about-us">
        <div class="about-us__image-container">
          <Image src="/images/salad.jpg" />
        </div>
        <div class="about-us__info">
          <h2 class="about-us__header">{{ headerTitle }}</h2>
          <p class="about-us__text">{{ aboutUsText }}</p>
          <NuxtLink to="/contact" class="btn">{{ buttonText }}</NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assests/styles/variables";
@import "../assests/styles/main";

.about-us {
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: $font-family;
  color: $black;
  margin-top: -15px;

  @media #{$media-mobile} {
    flex-direction: column-reverse;
    margin-top: 20px;
  }

  @media #{$media-tablet} {
    flex-direction: column-reverse;
    margin-top: 20px;
  }

  &__image-container {
    margin-right: 20px;

    @media #{$media-tablet} {
      margin-top: 20px;
      width: 100%;
    }

    @media #{$media-mobile} {
      width: 100%;
      margin-top: 20px;
    }
  }

  img {
    display: flex;
    border-radius: 8px;

    @media #{$media-mobile} {
      width: 100%;
      padding-left: 10px;
    }

    @media #{$media-tablet} {
      display: flex;
      justify-content: center;
      width: 100%;
      padding-left: 10px;
    }
  }

  &__header {
    font-size: 35px;
  }
}
</style>