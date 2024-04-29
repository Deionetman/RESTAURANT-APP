<script setup>
defineProps([
  "heroTitle",
  "heroText",
  "buttonText",
  "src",
  "to",
  "showImgContainer",
]);
</script>

<template>
  <div class="container">
    <div class="hero">
      <div class="hero__container-left">
        <h1 class="hero__title">
          {{ heroTitle }}
        </h1>
        <p class="hero__text">
          {{ heroText }}
        </p>
        <NuxtLink class="hero__button" :to="to">{{ buttonText }}</NuxtLink>
      </div>
      <div class="hero__container-right" v-if="showImgContainer">
        <Image class="hero__container-img" :src="src" />
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assests/styles/variables";
@import "../assests/styles/main";
.hero {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  margin: 0 auto;
  font-family: $font-family;

  @media #{$media-mobile} {
    display: flex;
    flex-direction: column;
  }

  &__container-left {
    margin-right: 20px;

    @media #{$media-mobile} {
      margin: 0;
    }
  }

  &__title {
    font-size: 40px;
    color: $black;
    margin: 20px 0;

    @media #{$media-mobile} {
      font-size: 30px;
    }
  }

  &__text {
    font-size: 25px;
    margin: 10px 0 30px;

    @media #{$media-mobile} {
      font-size: 20px;
    }
  }

  &__button {
    border: none;
    color: white;
    background: $pink;
    padding: 15px 50px;
    border-radius: 20px;
    font-size: 14px;
    font-weight: 700;
    text-decoration: none;
    font-family: $font-family;

    @media #{$media-mobile} {
      display: block;
      text-align: center;
    }
  }

  &__container-right {
    @media #{$media-tablet} {
      padding-left: 20px;
    }

    @media #{$media-mobile} {
      padding: 0;
    }
  }

  &__container-img {
    @media #{$media-mobile} {
      display: flex;
      flex-direction: column;
      justify-content: center;
      width: 150px;
      margin-top: 50px;
    }

    @media #{$media-tablet} {
      width: 300px;
    }
  }
}
</style>
