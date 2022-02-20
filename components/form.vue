<template>
  <div class="form-wrap" id="form">
    <div class="form__content">
      <p class="form__title">
        <span>Sign Up</span> and find the best place to rest while traveling
      </p>
      <form class="form">
        <div
          data-aos="fade-up"
          data-aos-duration="300"
          data-aos-easing="ease-in-out"
          data-aos-once="true"
        >
          <Input :input="input.firstName" />
        </div>
        <div
          data-aos="fade-up"
          data-aos-duration="300"
          data-aos-easing="ease-in-out"
          data-aos-once="true"
        >
          <Input :input="input.secondName" />
        </div>
        <div class="select">
          <div
            data-aos="fade-up"
            data-aos-duration="600"
            data-aos-easing="ease-in"
            data-aos-once="true"
          >
            <Select :countries="countries" />
          </div>
        </div>
        <div
          data-aos="fade-up"
          data-aos-duration="600"
          data-aos-easing="ease-in-out"
          data-aos-once="true"
        >
          <Input :input="input.phoneNumber" />
        </div>
        <div
          data-aos="fade-up"
          data-aos-duration="900"
          data-aos-easing="ease-in-out"
          data-aos-once="true"
        >
          <Input :input="input.password" />
        </div>
        <div
          data-aos="fade-up"
          data-aos-duration="900"
          data-aos-easing="ease-in-out"
          data-aos-once="true"
        >
          <Input class="confirm-password" :input="input.confirmPassword" />
          <span id="message">{{
            validateInput(
              this.input.confirmPassword.nameInput,
              this.input.confirmPassword.value
            )
          }}</span>
        </div>
        <div
          data-aos="fade-up"
          data-aos-duration="1200"
          data-aos-easing="ease-in-out"
          data-aos-once="true"
        >
          <Input :input="input.email" />
        </div>
      </form>
      <div
        data-aos="fade-up"
        data-aos-duration="1500"
        data-aos-easing="ease-in-out"
        data-aos-once="true"
      >
        <button class="form__btn" type="button" @click="submitHandler">
          Sign Up
        </button>
      </div>
    </div>
    <p class="log-in">If you have an account, <a href="">Log In</a></p>
  </div>
</template>

<script>
import AOS from "aos";
import "aos/dist/aos.css";
import Input from "~/components/input.vue";
import Select from "~/components/select.vue";
import countries from "~/components/country.js";
export default {
  mounted() {
    AOS.init({});
  },
  components: {
    Input,
    Select,
  },
  methods: {
    submitHandler() {
      setTimeout(function () {
        this.$refs.message.style.display = "none";
      }, 4000);
    },
    validateInput(type, value) {
      this.formValidationsError = value;
      switch (type) {
        case "confirmPassword":
          if (value) {
            if (value !== this.input.password.value) {
              console.log(
                "value=>",
                value,
                "password=>",
                this.input.password.value
              );
              this.input.confirmPassword.errorText = "Password does not match";
            } else if (value === this.input.password.value) {
              this.input.confirmPassword.errorText = "";
            }
          }
          break;
      }
    },
  },
  data: () => ({
    countries: countries,
    input: {
      firstName: {
        idInput: "firstName",
        typeInput: "text",
        nameInput: "firstName",
        labelText: "First Name",
        textInput: "First Name",
        icon: require("~/assets/icons/first-name_icon.svg"),
        required: true,
        value: "",
        errorText: "",
      },
      secondName: {
        idInput: "secondName",
        typeInput: "text",
        nameInput: "secondName",
        labelText: "Second Name",
        textInput: "Second Name",
        icon: require("~/assets/icons/second-name_icon.svg"),
        required: true,
        value: "",
        errorText: "",
      },
      phoneNumber: {
        idInput: "phoneNumber",
        typeInput: "tel",
        nameInput: "phoneNumber",
        labelText: "Phone",
        textInput: "Phone",
        value: "",
        errorText: "",
        icon: require("~/assets/icons/phone_icon.svg"),
      },
      password: {
        idInput: "password",
        typeInput: "password",
        nameInput: "password",
        labelText: "Password",
        textInput: "Password",
        value: "",
        errorText: "",
        icon: require("~/assets/icons/password_icon.svg"),
      },
      confirmPassword: {
        idInput: "confirmPassword",
        typeInput: "password",
        nameInput: "confirmPassword",
        labelText: "Confirm Password",
        textInput: "Confirm Password",
        value: "",
        errorText: "",
        icon: require("~/assets/icons/confirm-password_icon.svg"),
      },
      email: {
        idInput: "email",
        typeInput: "text",
        nameInput: "email",
        labelText: "Email",
        textInput: "Email",
        icon: require("~/assets/icons/email_icon.svg"),
        required: true,
        value: "",
        errorText: "",
      },
    },
  }),
};
</script>

<style lang="scss" scoped>
.form {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  width: 43.75vw;
  @media screen and (min-width: 360px) and (max-width: 575px) {
    display: block;
  }
  &-wrap {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    width: 100%;
    height: 100vh;
    background-image: url(~/assets/bg-forms/section_2-svg_1.svg),
      url(~/assets/bg-forms/section_2-svg_2.svg),
      url(~/assets/bg-forms/section_2-svg_3.svg), url(~/assets/img-bgs/bg-2.jpg);
    background-size: auto, auto, auto, cover;
    background-repeat: no-repeat;
    background-position: -2vw 26.667vw, right -4.5vw top 9.514vw,
      right 22.639vw bottom -2.3vw, center;
    @media screen and (min-width: 360px) and (max-width: 575px) {
      padding: 27.8vw 4.167vw 15.556vw;
      height: auto;
      background-size: 16.667vw 22.939vw, 31.667vw 24.85vw, 29.722vw 29.219vw,
        cover;
      background-position: -5.3vw 32.944vw, right -9vw top 1.389vw,
        right -8.361vw bottom 0, center;
    }
  }
  &__title {
    margin-bottom: 3.819vw;

    font-weight: 500;
    font-size: 1.667vw;
    line-height: 1.944vw;
    @media screen and (min-width: 360px) and (max-width: 575px) {
      font-size: 5.278vw;
      line-height: 6.389vw;
      text-align: center;
      margin-bottom: 8.333vw;
    }
    span {
      color: #6ceec7;
    }
  }
  &__btn {
    display: flex;
    padding: 1.111vw 3.472vw;
    margin-top: 1vw;
    font-family: "Rubik";
    font-weight: 500;
    font-size: 1.319vw;
    line-height: 1.597vw;
    text-align: center;

    border: 0.139vw solid #6ceec7;
    border-radius: 0.347vw;
    background: #6ceec7;
    color: black;
    cursor: pointer;
    transition: 0.3s;
    @media screen and (min-width: 360px) and (max-width: 575px) {
      margin-bottom: 16.667vw;
      padding: 4.444vw 37vw;
      border-radius: 1.389vw;
      font-size: 4.444vw;
      line-height: 5.278vw;
    }

    &:hover {
      background: transparent;
      color: #6ceec7;
    }
  }
}
.log-in {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  margin-bottom: 2.083vw;
  text-align: center;
  font-size: 1.042vw;
  line-height: 1.25vw;

  color: #e0e0e0;
  @media screen and (min-width: 360px) and (max-width: 575px) {
    margin-bottom: 15.556vw;
    font-size: 4.167vw;
    line-height: 5vw;
    white-space: nowrap;
  }

  a {
    padding-bottom: 0.208vw;
    color: #6ceec7;
    cursor: pointer;
    border-bottom: 0.069vw solid #6ceec7;
    opacity: 0.8;
    transition: 0.3s;
    &:hover {
      opacity: 1;
    }
  }
}
.confirm-password {
  margin-left: 2vw;
  @media screen and (min-width: 360px) and (max-width: 575px) {
    margin-left: 0;
  }
}
.select {
  position: static;
  z-index: 9;
  @media screen and (min-width: 360px) and (max-width: 575px) {
    position: relative;
  }
}
</style>
