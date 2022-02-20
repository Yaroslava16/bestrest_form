<template>
  <div class="input-wrap">
    <input
      class="input__input"
      :id="input.idInput"
      v-model.trim="input.value"
      :placeholder="input.textInput"
      :type="input.typeInput"
      :name="input.nameInput"
      :style="{ 'background-image': `url('${input.icon}')` }"
    />
    <label class="input__label" for="(input.idInput)">
      {{ input.labelText }}</label
    ><span class="input__error-text" id="message">{{
      validateInput(input.nameInput, input.value)
    }}</span>
  </div>
</template>

<script>
export default {
  props: ["input"],
  data() {
    return { password: "", formValidationsError: "" };
  },
  methods: {
    validateInput(type, value) {
      this.formValidationsError = value;
      switch (type) {
        case "phoneNumber":
          if (value.length < 1) {
            this.input.errorText = "Fill in the field";
          } else if (value.length >= 1) {
            this.input.errorText = "";
          }
          break;

        case "firstName":
          if (value.length > 0 && value.length < 2) {
            this.input.errorText = "The name must be more than 2 characters";
            // setTimeout(function () {
            //   document.getElementById("message").style.display = "none";
            // }, 4000);
          } else if (value.length >= 2) {
            this.input.errorText = "";
          }
          break;

        case "secondName":
          if (value.length > 0 && value.length < 2) {
            this.input.errorText = "The name must be more than 2 characters";
          } else if (value.length >= 2) {
            this.input.errorText = "";
          }
          break;

        case "password":
          if (value) {
            const validPassword = /(?=.*[0-9])+(?=.*[!@#$%^&*])+(?=.*[a-z])/;
            this.password = value;
            if (validPassword.test(value)) {
              this.input.errorText = "";
            } else {
              this.input.errorText =
                "Password must have 1 letter, 1 number and one symbol";
            }
          }
          break;
        case "email":
          if (value) {
            const validEmail = /(?=.*[@])+(?=.*[.])/;
            if (validEmail.test(value)) {
              this.input.errorText = "";
            } else {
              this.input.errorText = "Email is not correct";
            }
          }
          break;
      }

      return this.input.errorText;
    },
    clearError() {
      return (this.input.errorText = "");
    },
  },
};
</script>

<style lang="scss" scoped>
.input {
  &-wrap {
    padding-bottom: 6.083vw;
    width: 20.833vw;
    position: relative;
    @media screen and (min-width: 360px) and (max-width: 575px) {
      width: 100%;
      padding-bottom: 24vw;
    }
  }
  &__label {
    position: absolute;
    top: 50%;
    left: 0;
    transform: translate(0, -50%);
    padding: 0.828vw 1.111vw 0.764vw 3.472vw;
    font-size: 1.319vw;
    line-height: 1.597vw;
    // margin-bottom: 1.389vw;
    color: #e0e0e0;
    transition: 0.3s;
    @media screen and (min-width: 360px) and (max-width: 575px) {
      padding: 0.828vw 1.111vw 1.764vw 14vw;
      white-space: nowrap;
      font-size: 5.278vw;
      line-height: 6.389vw;
    }
  }
  &__input {
    position: absolute;
    top: 50%;
    left: 0;
    transform: translate(0, -54%);
    width: 20.833vw;
    height: 3.889vw;
    border-radius: 0.347vw;
    border: 0.069vw solid #ffffff;
    padding: 1.828vw 1.111vw 0.6vw 3.472vw;
    font-size: 1.319vw;
    line-height: 1.597vw;
    background: rgba(0, 0, 0, 0.2);
    background-repeat: no-repeat;
    background-position: 1.111vw 1.111vw;
    background-size: 1.667vw;
    color: #e0e0e0;
    cursor: pointer;
    outline: none;
    transition: 0.3s;

    @media screen and (min-width: 360px) and (max-width: 575px) {
      padding: 5vw 3.111vw 1.6vw 13.9vw;
      width: 91.667vw;
      height: 15.556vw;
      border-radius: 1.389vw;
      font-size: 5.278vw;
      line-height: 6.389vw;
      background-size: 6.667vw;
      background-position: 4.111vw 4.111vw;
    }
    &:hover,
    &:focus {
      border: 0.069vw solid #6ceec7;
      cursor: pointer;
    }
  }
  &__input {
    &::placeholder {
      color: transparent;
    }
    &:not(:placeholder-shown) + label,
    &:focus + label {
      margin-top: -0.8vw;
      font-size: 0.764vw;
      line-height: 0.903vw;
      color: #6ceec7;
      @media screen and (min-width: 360px) and (max-width: 575px) {
        margin-top: -2.8vw;
        font-size: 2.964vw;
        line-height: 1.903vw;
      }
    }
  }

  &__error-text {
    position: absolute;
    bottom: 0;
    right: 0;
    font-size: 0.694vw;
    line-height: 0.833vw;
    color: #da5050;

    @media screen and (min-width: 360px) and (max-width: 575px) {
      right: -47vw;
      font-size: 2.694vw;
      line-height: 2.833vw;
      white-space: nowrap;
    }
  }
}
</style>
