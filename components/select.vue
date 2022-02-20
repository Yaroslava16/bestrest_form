<template>
  <div class="select">
    <button
      type="button"
      class="select__toggle"
      name="arrow"
      value=""
      data-select="toggle"
      @click="onClickSelect()"
      :class="{
        'select--active': optionsVisible,
        'select__toggle--active': countryChoose,
      }"
    >
      Country
    </button>
    <span class="select__country">{{ chooseCountry }}</span>
    <div v-if="optionsVisible" class="select__dropdown">
      <ul class="select__options">
        <li
          class="select__option"
          v-for="(country, i) in countries"
          :key="i"
          data-select="option"
          @click="onClickCountry(country)"
        >
          {{ country.name }}
        </li>
      </ul>
    </div>
    <!-- <span class="select__error-text">{{ validateSelect(chooseCountry) }}</span> -->
  </div>
</template>

<script>
export default {
  data: () => ({
    optionsVisible: false,
    chooseCountry: "",
    countryChoose: false,
  }),
  props: {
    countries: [],
  },
  methods: {
    // validateSelect(value) {
    //   console.log(value);
    //   switch (value) {
    //     case "country":
    //       if ((value.length < 1)) {
    //         country.errorText = "Fill in the field";
    //       } else if (value.length >= 1) {
    //         country.errorText = "";
    //       }
    //       break;
    //   }
    // },
    onClickSelect() {
      this.optionsVisible = !this.optionsVisible;
    },
    onClickCountry(country) {
      this.countryChoose = true;
      this.chooseCountry = country.name;
    },
  },
};
</script>

<style lang="scss" scoped>
.select {
  position: relative;
  width: 20.833vw;
  padding-top: 1vw;
  background-image: url(~/assets/icons/country_icon.svg);
  background-size: 1.667vw;
  background-repeat: no-repeat;
  background-position: 1.111vw 2.2vw;
  @media screen and (min-width: 360px) and (max-width: 575px) {
    padding-bottom: 5vw;
    border-radius: 1.389vw;
    background-size: 6.667vw;
    background-position: 4.111vw 5.5vw;
    font-size: 5.278vw;
    line-height: 6.389vw;
  }
  &--active {
    &::after {
      content: "";
      width: 1.667vw;
      height: 1.667vw;
      background-size: cover;
      background-image: url("~/assets/icons/select-arrow_icon.svg");
      transform: rotate(180deg);
      transition: all 0.3s ease-in-out;
      @media screen and (min-width: 360px) and (max-width: 575px) {
        width: 6.667vw;
        height: 6.667vw;
      }
    }
  }
  &__country {
    position: absolute;
    top: 50%;
    left: 0;
    transform: translate(0, -50%);
    padding: 0.828vw 1.111vw 0.764vw 3.472vw;
    font-size: 1.319vw;
    line-height: 1.597vw;
    color: #e0e0e0;
    transition: 0.3s;

    @media screen and (min-width: 360px) and (max-width: 575px) {
      padding: 0.828vw 1.111vw 2.764vw 14.5vw;
      font-size: 5.278vw;
      line-height: 6.389vw;
      white-space: nowrap;
    }
  }
}

.select__toggle {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.311vw 1.111vw 1.111vw 3.472vw;

  width: 100%;
  height: 3.889vw;
  font-family: "Rubik";
  font-weight: 300;
  font-size: 1.319vw;
  line-height: 1.597vw;
  user-select: none;

  background: rgba(0, 0, 0, 0.2);
  border: 0.069vw solid #ffffff;
  border-radius: 0.347vw;
  color: #e0e0e0;
  cursor: pointer;
  @media screen and (min-width: 360px) and (max-width: 575px) {
    padding: 1.828vw 2.111vw 4.564vw 14vw;
    width: 91.667vw;
    height: 15.556vw;
    border-radius: 1.389vw;
    font-size: 5.278vw;
    line-height: 6.389vw;
  }
  &:hover,
  &:focus {
    border: 0.069vw solid #6ceec7;
    cursor: pointer;
  }

  &::after {
    content: "";
    width: 1.667vw;
    height: 1.667vw;
    background-size: cover;
    background-image: url("~/assets/icons/select-arrow_icon.svg");
    @media screen and (min-width: 360px) and (max-width: 575px) {
      width: 6.667vw;
      height: 6.667vw;
    }
  }
  &:focus {
    outline: none;
  }
  &--active {
    padding-top: 0;
    font-size: 0.764vw;
    line-height: 0.903vw;
    color: #6ceec7;
     @media screen and (min-width: 360px) and (max-width: 575px) {
        font-size: 2.964vw;
        line-height: 1.903vw;
     }
    &::after {
      margin-top: 1.3vw;
    }
  }
}

.select__toggle--active + span {
  margin-top: 0.9vw;
}

.select__dropdown {
  display: block;
  position: absolute;
  top: 5.1vw;
  left: 0;
  right: 0;
  padding: 1.458vw 1.597vw;
  border: 1px solid #fff;
  max-height: 11.042vw;
  overflow-y: auto;
  border-radius: 0.3125rem;
  z-index: 2;
  background-color: #fff;

  box-shadow: 0px 0.278vw 1.042vw rgba(0, 0, 0, 0.3);
  border-radius: 0.347vw;
  @media screen and (min-width: 360px) and (max-width: 575px) {
    top: 17vw;
    width: 91.667vw;
    padding: 4.458vw 4.597vw;
    max-height: 44.167vw;
    border-radius: 1.389vw;
  }
  &::-webkit-scrollbar {
    width: 0;
  }
}

.select__options {
  margin: 0;
  padding: 0;
  list-style: none;
}

.select__option {
  padding: 0 0 1.042vw 0;
  color: #5e5e5e;
  transition: all 0.3s ease-in-out;
  cursor: pointer;
  @media screen and (min-width: 360px) and (max-width: 575px) {
    padding: 0 0 5.042vw 0;
    font-size: 4.167vw;
    line-height: 5vw;
  }
  &:hover,
  &:focus {
    color: black;
    margin-left: 0.756vw;
    @media screen and (min-width: 360px) and (max-width: 575px) {
      margin-left: 3vw;
    }
  }
  &:last-child {
    margin-bottom: 0;
    padding-bottom: 0;
  }
}

.select__option_selected {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
