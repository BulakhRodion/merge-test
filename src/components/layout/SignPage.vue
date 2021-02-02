<template>
  <div class="merge-signin">
    <div class="merge-signin__col merge-signin__col--slider">
      <a-carousel
        dotsClass="merge-signin__carousel-dots"
        class="merge-signin__carousel"
      >
        <div
          class="merge-signin__carousel-item"
          v-for="slide in slides"
          :key="slide.id"
        >
          <div class="merge-signin__img-wrapper">
            <img
              :src="require(`@/assets/signIn/${slide.image}`)"
              class="merge-signin__carousel-item-img"
            />
          </div>
          <h2 class="merge-signin__carousel-item-title">{{ slide.title }}</h2>
          <p class="merge-signin__carousel-item-text">{{ slide.text }}</p>
        </div>
      </a-carousel>
    </div>
    <div class="merge-signin__col merge-signin__col--form">
      <the-icons icon="merge" class="merge-signin__icon" />
      <h1 class="merge-signin__title">Sign In</h1>
      <div class="merge-signin__registration-wrapper">
        <p class="merge-signin__registration-text">Don’t have an account?</p>
        <the-sign-modal />
      </div>
      <the-sign-form />
      <ul class="merge-signin__links-list">
        <li v-for="link in links" :key="link" class="merge-signin__list-item">
          <a href="#" class="merge-signin__link">{{ link }}</a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import TheSignForm from "../common/TheSignForm.vue";
import TheSignModal from "../common/TheSignModal.vue";
import TheIcons from "../icons/TheIcons.vue";
export default {
  components: { TheSignForm, TheSignModal, TheIcons },
  data() {
    return {
      slides: [
        {
          id: 1,
          title: "Tokenplace",
          text: "Multi-exchange Trading Terminal",
          image: "sign-first-slide.png",
        },
        {
          id: 2,
          title: "Fund Platform",
          text: "Hedge funds wealth management",
          image: "sign-second-slide.png",
        },
        {
          id: 3,
          title: "Tokenplace",
          text:
            "It gives data managers the power to efficiently manage quality data to ensure database lock readiness.",
          image: "sign-third-slide.png",
        },
      ],
      links: ["Contact", "Privacy", "Terms"],
    };
  },
};
</script>

<style lang="scss">
.merge-signin {
  display: flex;
  min-height: 100vh;
  padding: 20px;
  &__col {
    display: flex;
    justify-content: center;
    flex-direction: column;
    &--slider {
      min-width: 0;
      position: relative;
      background-color: $primary-blue;
      flex-basis: 55%;
      max-width: 55%;
      border-radius: 15px;
      padding: 0 70px;
      overflow: hidden;
      &::before {
        content: "";
        position: absolute;
        width: 600px;
        height: 400px;
        background-color: $secondary-blue;
        top: -10px;
        left: -224px;
        transform: rotate(150deg);
      }
      &::after {
        content: "";
        position: absolute;
        width: 600px;
        height: 400px;
        z-index: 0;
        background-color: $secondary-blue;
        bottom: -10px;
        right: -310px;
        transform: rotate(136deg);
      }
      @media screen and (max-width: 800px) {
        display: none;
      }
    }
    &--form {
      align-items: flex-start;
      justify-content: flex-start;
      flex-basis: 45%;
      max-width: 45%;
      padding: 30px 120px 50px 80px;
      @media screen and (max-width: 1300px) {
        flex-basis: 50%;
        max-width: 50%;
        padding-right: 30px;
      }
      @media screen and (max-width: 800px) {
        flex-basis: 100%;
        max-width: 100%;
        padding: 10px 20px;
      }
    }
  }
  &__carousel {
    z-index: 2;
  }
  &__carousel-item {
    display: flex !important;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    padding-bottom: 40px;
  }
  &__img-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    margin-bottom: 60px;
    max-width: 512px;
    width: 100%;
    height: 332px;
    img {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-size: cover;
    }
  }
  &__carousel-item-title {
    font-size: $H200;
    font-weight: 600;
    color: $white;
    margin-bottom: 15px;
    text-align: center;
  }
  &__carousel-item-text {
    font-size: $H140;
    font-weight: 600;
    color: $white;
    text-align: center;
    max-width: 512px;
  }
  &__icon {
    fill: $N10;
    margin-bottom: 100px;
    transition: fill 0.4s ease;
    &:hover {
      fill: $primary-blue;
    }
    @media screen and (max-width: 800px) {
      margin-bottom: 40px;
      &:hover:not() {
        fill: $primary-blue;
      }
    }
  }
  &__title {
    font-size: $H280;
    font-weight: 700;
    color: $primary-black;
    margin-bottom: 15px;
  }
  &__registration-wrapper {
    display: flex;
    margin-bottom: 60px;
    @media screen and (max-width: 800px) {
      margin-bottom: 30px;
    }
  }
  &__registration-text {
    font-size: $H140;
    font-weight: 600;
    color: $primary-black;
    margin-right: 10px;
    @media screen and (max-width: 760px) {
      font-size: $H120;
    }
    &--link {
      color: $primary-blue;
      margin-right: 0;
      transition: color 0.4s ease;
      &:hover {
        color: darken($color: $primary-blue, $amount: 10%);
      }
    }
  }
  &__registration-link-wrapper {
    display: flex;
    align-items: flex-start;
  }
  &__form {
    width: 100%;
    margin-bottom: 220px;
    @media screen and (max-width: 800px) {
      margin-bottom: 40px;
    }
  }
  &__form-item {
    margin-bottom: 30px;
  }
  &__input {
    height: 54px;
    &--pass {
      padding-right: 184px;
      @media screen and (max-width: 1100px) {
        padding-right: 10px;
      }
    }
  }
  &__forget-link {
    font-size: $H140;
    font-weight: 600;
    line-height: 32px;
    position: absolute;
    top: -8px;
    right: 16px;
    @media screen and (max-width: 1100px) {
      position: relative;
      top: 0;
      right: 0;
    }
  }
  &__login-btn {
    width: 100%;
    height: 54px;
    background-color: $primary-blue;
    border-color: $primary-blue;
    box-shadow: 0px 6px 18px 0px rgba(0, 0, 0, 0.7);
    &:hover {
      background-color: darken($color: $primary-blue, $amount: 10%);
      border-color: darken($color: $primary-blue, $amount: 10%);
    }
  }
  &__links-list {
    display: flex;
    margin-bottom: 0;
  }
  &__list-item {
    font-size: $H140;
    font-weight: 600;
    margin-right: 25px;
    &:last-child {
      margin-right: 0;
    }
  }
  .ant-carousel .slick-dots li {
    margin-right: 45px;
    &:last-child {
      margin-right: 0;
    }
  }
  .ant-carousel .slick-dots li button {
    height: 8px;
    width: 8px;
    border-radius: 50%;
  }
  .ant-form-item-required {
    font-size: $H140;
    font-weight: 600;
    color: $primary-black;
    line-height: 0;
    &::before,
    &::after {
      display: none;
    }
  }
  .ant-form-explain {
    position: absolute;
    width: 100%;
    left: 0%;
    right: 0%;
    top: -50%;
    font-size: $H120;
    font-weight: 600;
    text-align: right;
  }
  .ant-input {
    height: 54px;
  }
  .has-error .ant-input {
    border-color: #f5222d !important;
  }
  .approved {
    border: 1px solid $green-color;
  }
}
</style>