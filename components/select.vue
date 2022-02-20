<template>
  <div class="select">
    <button
      type="button"
      class="select__toggle"
      name="car"
      value=""
      data-select="toggle"
      data-index="-1"
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
  background-repeat: no-repeat;
  background-position: 1.111vw 1.9vw;
  &--active {
    &::after {
      content: "";
      width: 1.667vw;
      height: 1.667vw;
      background-size: cover;
      background-image: url("~/assets/icons/select-arrow_icon.svg");
      transform: rotate(180deg);
      transition: all 0.3s ease-in-out;
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
  }
  &:focus {
    outline: none;
  }
  &--active {
    padding-top: 0;
    font-size: 0.764vw;
    line-height: 0.903vw;
    color: #6ceec7;
    &::after {
      margin-top: 1.3vw;
    }
  }
}

.select__toggle--active + span {
  margin-top: 0.5vw;
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
  &:hover,
  &:focus {
    color: black;
    margin-left: 0.756vw;
  }
  &:last-child {
    margin-bottom: 0;
    padding-bottom: 0;
  }
}

.select__option_selected {
  background-color: #e1f5fe;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.select__option_selected::after {
  content: "";
  width: 0.75rem;
  height: 0.75rem;
  color: #0277bd;
  background-size: cover;
  background-image: url('data:image/svg+xml,%3Csvg xmlns="http://www.w3.org/2000/svg" height="100" width="100" class="svg-inline--fa fa-check fa-w-16" data-icon="check" data-prefix="fas" aria-hidden="true"%3E%3Cpath d="M33.964 85.547l-32.5-32.251a4.935 4.935 0 010-7.017l7.071-7.017a5.027 5.027 0 017.071 0L37.5 60.987l46.894-46.534a5.028 5.028 0 017.07 0l7.072 7.017a4.935 4.935 0 010 7.017l-57.5 57.06a5.027 5.027 0 01-7.072 0z" fill="%230277bd"/%3E%3C/svg%3E');
}

.select__option:hover {
  background-color: #f5f5f5;
  cursor: pointer;
  transition: 0.2s background-color ease-in-out;
}
</style>
