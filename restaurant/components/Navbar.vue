<script setup>
import { ref } from "vue";

const toggleMobileMenu = ref(false);
</script>

<template>
  <!-- DESKTOP MENU -->
  <div class="navigation__container">
    <div class="navigation__logo-container">
      <NuxtLink to="/">
        <img src="/logos/foodora.svg" width="200" height="100" />
      </NuxtLink>
    </div>
    <nav>
      <ul class="navigation__items">
        <li class="navigation__item">
          <NuxtLink class="navigation__styling" to="/">Home</NuxtLink>
        </li>
        <li class="navigation__item">
          <NuxtLink class="navigation__styling" to="/menu">Menu</NuxtLink>
        </li>
        <li class="navigation__item">
          <NuxtLink class="navigation__styling" to="/about">About</NuxtLink>
        </li>
        <li class="navigation__item">
          <NuxtLink class="navigation__styling" to="/contact">Contact</NuxtLink>
        </li>
      </ul>
    </nav>
    <div class="navigation__account-details">
      <div class="navigation__account-icon-container">
        <Image src="/icons/loop.svg" />
      </div>
      <div class="navigation__account-icon-container">
        <Image src="/icons/mailbox.svg" />
      </div>
      <div class="navigation__login-container">
        <NuxtLink class="navigation__button">Login</NuxtLink>
      </div>
    </div>

    <!-- MOBILE MENU -->
    <div class="navigation__mobile-menu-toggle">
      <img
        @click="toggleMobileMenu = !toggleMobileMenu"
        class="navigation__mobile-menu-btn"
        src="/icons/burger-menu-right.svg"
      />
    </div>

    <div v-show="toggleMobileMenu" class="mobile-menu-is-open">
      <nav>
        <ul class="mobile-navigation__items">
          <li class="mobile-navigation__item">
            <NuxtLink class="mobile-navigation__styling" to="/">Home</NuxtLink>
          </li>
          <li class="mobile-navigation__item">
            <NuxtLink class="mobile-navigation__styling" to="/menu"
              >Menu</NuxtLink
            >
          </li>
          <li class="mobile-navigation__item">
            <NuxtLink class="mobile-navigation__styling" to="/about"
              >About</NuxtLink
            >
          </li>
          <li class="mobile-navigation__item">
            <NuxtLink class="mobile-navigation__styling" to="/contact"
              >Contact</NuxtLink
            >
          </li>
        </ul>
      </nav>
      <div class="mobile-navigation__account-details">
        <div class="mobile-navigation__account-icon-container">
          <Image src="/icons/loop.svg" />
        </div>
        <div class="mobile-navigation__account-icon-container">
          <Image src="/icons/mailbox.svg" />
        </div>
        <div class="mobile-navigation__login-container">
          <NuxtLink class="navigation__button">Login</NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assests/styles/variables";
@import "../assests/styles/main";
.navigation {
  &__container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 1200px;
    margin: 0 auto;
    padding: 10px;
    font-family: $font-family;
    color: $black;
    z-index: 5;
  }

  &__items {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
  }

  &__item {
    list-style-type: none;
    font-size: 17px;
    font-weight: 600;
    font-family: $font-family;

    @media #{$media-tablet} {
      display: none;
    }
  }

  &__styling {
    color: $black;
    text-decoration: none;

    &:hover {
      color: $pink;
      text-decoration: underline;
      text-underline-offset: 3px;
    }
  }

  &__account-details {
    display: flex;
    justify-content: space-between;
    align-items: center;

    @media #{$media-tablet} {
      display: none;
    }
  }

  &__account-icon-container {
    margin-right: 30px;

    &:hover {
      cursor: pointer;
    }
  }

  &__button {
    border: none;
    color: white;
    background-color: $pink;
    padding: 10px 30px;
    border-radius: 20px;
    font-size: 14px;
    font-weight: 700;
    font-family: $font-family;
    text-decoration: none;

    &:hover {
      cursor: pointer;
    }
  }

  &__mobile-menu-toggle {
    display: none;

    @media #{$media-tablet} {
      display: block;
    }
  }

  &__mobile-menu-btn {
    height: 40px;
    color: $pink;

    @media #{$media-desktop} {
      display: none;
    }
    @media #{$media-tablet} {
      display: block;
    }
  }
}

.mobile-menu-is-open {
  display: block;
  position: fixed;
  left: 0;
  top: 115px;
  right: 0;
  bottom: 0;
  border-top: 2px solid $light-grey;
  background: $white;
  height: 100%;
  width: 100%;
  z-index: 100;
}

.mobile-navigation {
  font-family: $font-family;

  &__items {
    margin-top: 0;
    padding-left: 10px;
  }

  &__item {
    border-bottom: 2px solid $light-grey;
    padding: 20px 0;
    margin-right: 10px;
    list-style: none;
    font-size: 17px;
    font-weight: 600;
    font-family: $font-family;
  }

  &__styling {
    color: $black;
    text-decoration: none;
  }

  &__account-details {
    display: flex;
    justify-content: flex-start;
    padding-left: 10px;
  }

  &__account-icon-container {
    margin-right: 15px;
  }
}

.router-link-exact-active {
  color: $pink;
  text-decoration: underline;
  text-underline-offset: 3px;
}
</style> 
