<script setup>
import { onMounted, ref, computed } from "vue";
import axiosClient from "../../axiosClient";
import store from "../../store";

const keyword = ref("");
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  store.dispatch("searchMeals", keyword.value);

  keyword.value = "";
}

onMounted(async () => {
  try {
    const response = await axiosClient.get("/list.php?i=list");
    return response.data;
  } catch (error) {
    throw error;
  }
});
</script>

<template>
  <div>
    <Banner bannerTitle="Our Menu" />
    <div class="container">
      <div class="menu">
        <div class="menu__input-wrapper">
          <div class="row">
            <div class="col-md-12">
              <Input
                type="text"
                placeholder="Search for meals..."
                v-model="keyword"
                @change="searchMeals"
                :showLabel="false"
              />
            </div>
          </div>
        </div>

        <div class="menu__container">
          <div v-for="meal of meals" :key="meal.idMeal">
            <div class="meal-card">
              <div class="meal-card__image-container">
                <img :src="meal.strMealThumb" :alt="meal.strMeal" />
              </div>
              <div class="meal-card__info">
                <h3 class="meal-card__title">{{ meal.strMeal }}</h3>
                <p class="meal-card__text">
                  Lorem, ipsum dolor sit amet consectetur adipisicing elit.
                  Ratione fugit necessitatibus aperiam quas minima tempora
                </p>
                <div class="meal-card__link-container">
                  <NuxtLink class="meal-card__yt-link btn" :to="meal.strYoutube"
                    >Youtube</NuxtLink
                  >
                  <NuxtLink class="meal-card__view-link" to=""
                    >Order meal</NuxtLink
                  >
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assests/styles/variables";
@import "../assests/styles/main.scss";

.menu {
  margin: 0 auto;
  font-family: $font-family;

  &__search-letter {
    font-size: 20px;
    color: $pink;
    text-decoration: none;

    @media #{$media-mobile} {
      display: none;
    }

    &:hover {
      text-decoration: underline;
      cursor: pointer;
    }
  }

  &__input-wrapper {
    width: 100%;
  }

  &__container {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-flow: row wrap;
    gap: 20px;
    margin: 30px 0;

    @media #{$media-mobile} {
      justify-content: flex-start;
    }

    @media #{$media-tablet} {
      justify-content: flex-start;
    }
  }

  input {
    width: 100%;
    padding: 10px;
    border: none;
  }
}

.meal-card {
  display: flex;
  flex-flow: column nowrap;
  text-decoration: none;
  width: 100%;
  max-width: 280px;
  font-family: $font-family;
  border: 1px solid $light-grey;
  border-radius: 22px 22px 0 0;
  box-shadow: 0 4px 14px rgba(0, 0, 0, 0.15);
  background: $white;
  transition: transform 0.2 ease-in-out;

  &:hover {
    transform: scale(1.02);  
    cursor: pointer;
  }

  &__image-container {
    position: relative;
    flex-shrink: 0;
    width: 100%;
    overflow: hidden;
    border: 1px solid $light-grey;
    border-radius: 22px 22px 0 0;
    aspect-ratio: 381/281;
  }

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 22px 22px 0 0;
  }

  &__info {
    display: flex;
    flex: 1 0 calc(100% - 285px);
    flex-flow: column nowrap;
    height: 100%;
    padding: 20px;
  }

  &__title {
    font-size: 20px;
    color: $black;
    margin: 0;
  }

  &__text {
    flex: 1 0 calc(100% - 200px);
    margin: 15px 0;
  }

  &__link-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: auto;
  }

  &__yt-link {
    background: $pink;
    text-decoration: none;
    color: $white;
    padding: 10px 20px;
  }

  &__view-link {
    color: $pink;
    padding: 10px 30px;
    border-radius: 20px;
    font-size: 14px;
    font-weight: 700;
    text-decoration: none;
  }
}

.meal-link {
  text-decoration: none;
  color: $black;

  display: flex;
  align-items: center;
  flex-flow: row wrap;
  gap: 20px;
  margin: 30px 0;

  @media #{$media-mobile} {
    justify-content: center;
  }
}
</style>