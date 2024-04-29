<script setup>
defineProps(['buttonText'])
</script>

<template>
    <button class="btn">{{ buttonText }}</button>
</template>

<style lang="scss" scoped>
@import "../assests/styles/variables";
@import "../assests/styles/main";

</style>