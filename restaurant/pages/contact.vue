<script setup>
import { ref } from "vue";
defineProps(["fullName", "email", "phoneNumber"]);

const fullName = ref("");
const email = ref("");
const phoneNumber = ref("");

const submitForm = () => {
  const LengthFullName = fullName.value.length;
  const lengthPhoneNumber = phoneNumber.value.length;

  if (LengthFullName > 3 && email && lengthPhoneNumber === 10) {
    alert("Succes, form is submitted!");
  } else {
    alert("Error, form is not submitted!");
  }

  fullName.value = "";
  email.value = "";
  phoneNumber.value = "";
};
</script>

<template>
  <div class="background-light-grey">
    <Banner bannerTitle="Contact" />
    <div class="container">
      <div class="contact">
        <div class="contact__container-left">
          <form @submit.prevent="submitForm">
            <Input
              label="Full Name*"
              type="text"
              placeholder="Elon Musk"
              :modelValue="fullName"
              @update:modelValue="(newValue) => (fullName = newValue)"
              :showLabel="true"
            />
            <span v-show="fullName < 3">
              Value has to be equal or greater than 3 characters
            </span>
            <Input
              label="Email*"
              type="email"
              placeholder="e.g. example@email.com"
              :modelValue="email"
              @update:modelValue="(newValue) => (email = newValue)"
              :showLabel="true"
            />
            <Input
              label="Phone"
              type="tel"
              :modelValue="phoneNumber"
              @update:modelValue="(newValue) => (phoneNumber = newValue)"
              :showLabel="true"
            />
            <span v-show="phoneNumber.length !== 10">
              Value has to be 10 characters
            </span>
            <div class="contact__container-btn">
              <Button buttonText="Send" />
            </div>
          </form>
        </div>
        <div class="contact__container-right">
          <Image src="/images/worldmap2.svg" />
        </div>
      </div>
    </div>
  </div>
</template>
 
<style lang="scss" scoped>
@import "../assests/styles/variables";
@import "../assests/styles/main";

.contact {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  padding: 60px 0;

  @media #{$media-mobile} {
    flex-direction: column;
    padding: 30px 0;
  }

  @media #{$media-tablet} {
    flex-direction: column;
    justify-content: center;
    padding: 30px 0;
  }

  &__container-left {
    display: flex;
    justify-content: center;
    width: 250px;
    margin-right: 20px;
    padding-right: 10px;

    @media #{$media-mobile} {
      margin: 0;
      padding: 0;
    }
  }

  &__container-btn {
    margin-top: 25px;
  }

  img {
    width: 700px;

    @media #{$media-mobile} {
      margin-top: 20px;
      width: 100%;
    }

    @media #{$media-tablet} {
      margin-top: 20px;
      width: 100%;
    }
  }

  span {
    font-family: $font-family;
    font-size: 14px;
    display: block;
    color: red;
    margin: 5px 0;
    font-weight: 700;
  }
}
</style>