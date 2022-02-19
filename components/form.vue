<template>
  <div class="form-wrap" id="form">
    <div class="form__content">
      <p class="form__title">
        <span>Sign Up</span> and find the best place to rest while traveling
      </p>
      <form class="form">
        <Input :input="input.firstName" />
        <Input :input="input.secondName" />
        <Input :input="input.phoneNumber" />
        <Input :input="input.password" />
        <Input :input="input.confirmPassword" />
        <span id="message">{{
          validateInput(
            this.input.confirmPassword.nameInput,
            this.input.confirmPassword.value
          )
        }}</span>
        <Input :input="input.email" />
        <button class="form__btn" type="button" @click="submitHandler">
          Sign Up
        </button>
      </form>
    </div>
    <p class="log-in">If you have an account, <a href="">Log In</a></p>
  </div>
</template>

<script>
import Input from "~/components/input.vue";
export default {
  components: {
    Input,
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
  }
  &__title {
    margin-bottom: 3.819vw;

    font-weight: 500;
    font-size: 1.667vw;
    line-height: 1.944vw;

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
</style>
