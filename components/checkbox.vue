<template>
  <div class="checkbox-wrap">
    <input class="checkbox" type="checkbox" id="checkbox" />
    <label class="checkbox__label" for="checkbox"
      >I agree to the &nbsp<a href="#">Terms & Conditions</a>
    </label>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.checkbox {
  position: absolute;
  margin: 0;
  opacity: 0;
  z-index: -1;
  &-wrap {
    display: flex;
    position: absolute;
    top: 2.3vw;
    left: -21vw;
    align-items: center;
    @media screen and (min-width: 360px) and (max-width: 575px) {
      position: static;
      margin-bottom: 14.722vw;
      margin-top: 5.389vw;
      display: block;
      left: 0;
    }
  }
  &__label {
    font-size: 1.042vw;
    line-height: 1.25vw;
    color: #e0e0e0;
    cursor: default;
    @media screen and (min-width: 360px) and (max-width: 575px) {
      font-size: 4.167vw;
      line-height: 5vw;
      white-space: nowrap;
    }
    a {
      color: #6ceec7;
      border-bottom: 0.069vw solid #6ceec7;
      &:hover {
        border-bottom: 0.069vw solid #fff;
      }
    }
  }
}
.checkbox + label {
  display: inline-flex;
  align-items: center;
  user-select: none;
  cursor: default;
  &::before {
    content: "";
    display: inline-block;
    margin-right: 0.764vw;
    width: 1.389vw;
    height: 1.389vw;
    flex-shrink: 0;
    flex-grow: 0;
    border: 0.069vw solid #6ceec7;
    border-radius: 0.208vw;
    cursor: pointer;
    @media screen and (min-width: 360px) and (max-width: 575px) {
      margin-right: 3.056vw;
      width: 5.556vw;
      height: 5.556vw;
      border-radius: 0.833vw;
    }
  }
}

.checkbox:checked + label::before {
  border-color: #6ceec7;
  background-color: #6ceec7;
  background-image: url("~/assets/icons/check_icon.svg");
  background-size: cover;
}
.checkbox:not(:disabled):not(:checked) + label:hover::before {
  background: #6ceec7;
}
</style>
