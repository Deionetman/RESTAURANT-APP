<script setup>
defineProps(["bannerTitle"]);
</script>


<template>
  <div class="background-pink">
    <div class="banner">
      <h2 class="banner__title">{{ bannerTitle }}</h2>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assests/styles/variables";

.banner {
  color: $white;
  font-family: $font-family;
  text-align: center;
  padding: 15px;
  margin-bottom: 15px;

  &__title {
    margin: 0;
  }
}
</style>