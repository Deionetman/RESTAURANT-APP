<script setup>
defineProps(["label", "type", "name", "placeholder", "modelValue", "showLabel"]);

defineEmits(["update:modelValue"]);
</script>

<template>
  <div class="input">
    <div v-show="showLabel" class="input__label-container">
      <label>{{ label }}</label>
    </div>
    <div class="input__container">
      <input
        :type="type"
        :name="name"
        :placeholder="placeholder"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
      />
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assests/styles/variables";
@import "../assests/styles/main";

.input {
  font-family: $font-family;

  &__label-container {
    margin: 10px 0;
  }

  &__container {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    padding: 15px;
    background: $white;
    outline: 3px solid $light-grey;

    @media #{$media-mobile} {
      width: 100%;
    }
  }
}

input {
  width: 100%;
  border: none;
  font-size: 18px;
  font-family: $font-family;
  font-weight: 600;

  &:focus {
    outline: none;
    width: 100%;
  }
}
</style>