<template>
  <div class="grettings-wrap">
    <div class="grettings__content">
      <img class="grettings__logo" src="~assets/logo.svg" alt="" />
      <h1 class="grettings__title">
        Find the<span> best place</span><br />
        <span>to rest</span> while traveling
      </h1>
      <button
        class="grettings__btn"
        v-scroll-to="{
          el: '#form',
          duration: 300,
          easing: 'linear',
        }"
      >
        Registration
      </button>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.grettings-wrap {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100vh;
  background-image: url(~/assets/bg-forms/section_1-svg_2.svg),
    url(~/assets/bg-forms/section_1-svg_1.svg),
    url(~/assets/bg-forms/section_1-svg_3.svg), url(~/assets/img-bgs/bg-1.jpg);
  background-size: auto, auto, auto, cover;
  background-repeat: no-repeat;
  background-attachment: scroll, scroll, scroll, fixed;
  background-position: -4vw 17.847vw, right 17.847vw top -3vw,
    right -3vw bottom 2vw, center;
  @media screen and (min-width: 360px) and (max-width: 575px) {
    background-size: 27.5vw 21.667vw, 23.889vw 33.889vw, 25.833vw, cover;
    background-position: right -8.5vw top 50vw, left -7vw top 3.611vw,
      left -7vw bottom 10.833vw, center;
  }
}
.grettings {
  &__logo {
    margin: 0 auto 2.778vw;
    @media screen and (min-width: 360px) and (max-width: 575px) {
      width: 33.333vw;
      height: 8.333vw;
      margin-bottom: 5.556vw;
    }
  }
  &__title {
    margin: 0 auto 2.778vw;
    // width: 45.278vw;
    font-size: 4.306vw;
    line-height: 5.069vw;
    text-align: center;
    @media screen and (min-width: 360px) and (max-width: 575px) {
      font-size: 8.333vw;
      line-height: 10vw;
      margin-bottom: 5.556vw;
    }
    span {
      color: #6ceec7;
    }
  }
  &__btn {
    display: flex;
    margin: 0 auto;
    padding: 1.111vw 3.472vw;

    font-family: Rubik;
    font-weight: 500;
    font-size: 1.319vw;
    line-height: 1.597vw;
    text-align: center;

    border: 0.139vw solid #6ceec7;
    border-radius: 0.347vw;
    color: #6ceec7;
    cursor: pointer;
    transition: 0.3s;
    @media screen and (min-width: 360px) and (max-width: 575px) {
      padding: 4.167vw 32.5vw;
      border-radius: 1.389vw;
      font-size: 4.444vw;
      line-height: 5.278vw;
    }
    &:hover {
      background: #6ceec7;
      color: black;
    }
  }
}
</style>
