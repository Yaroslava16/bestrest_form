<template>
  <div>
    <div class="input-wrap">
      <!-- <label class="input__label" for="(input.idInput)">
      <span>{{ input.labelText }}</span>
      
    </label> -->
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
      ><span class="input__error-text">{{
        validateInput(input.nameInput, input.value)
      }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: ["input"],
  data() {
    return {
      formValidationsError: "",
    };
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
      }

      return this.input.errorText;
    },
  },
};
</script>

<style lang="scss" scoped>
.input {
  &-wrap {
    margin-bottom: 2.083vw;
    width: 20.833vw;
    position: relative;
    display: flex;
    flex-direction: column;

    input:focus + label,
    input:valid + label {
      top: 30%;
      font-size: 0.764vw;
      line-height: 0.903vw;
      color: #6ceec7;
      transition: 0.3s;
    }
    label,
    input:not(:focus) + label {
      position: absolute;
      top: 50%;
      left: 20%;
      transform: translate(-10%, -54%);
      font-size: 1.319vw;
      line-height: 1.597vw;
      margin-bottom: 1.389vw;
    }
  }

  &__input {
    width: 20.833vw;
    height: 3.889vw;
    border-radius: 0.347vw;
    border: 0.069vw solid #ffffff;
    padding: 1.828vw 1.111vw 0.764vw 3.472vw;
    margin-bottom: 0.417vw;
    transition: 0.2s;
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
    &::placeholder {
      opacity: 0;
    }
    &:hover,
    &:focus {
      border: 0.069vw solid #6ceec7;
      cursor: pointer;
    }
  }
  &__error-text {
    font-size: 0.694vw;
    line-height: 0.833vw;
    text-align: right;
    color: #da5050;
  }
}
</style>
