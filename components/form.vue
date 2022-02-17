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
    },
  }),
};
</script>

<style lang="scss" scoped>
.form {
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
