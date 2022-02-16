<template>
  <div class="form" id="form">
    <p class="log-in">If you have an account, <a href="">Log In</a></p>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.form {
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
