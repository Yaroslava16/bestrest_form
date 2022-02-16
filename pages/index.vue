<template>
  <div>
    <Greetings @scroll="goTo('form')" />
    <Form />
  </div>
</template>

<script>
import Greetings from "~/components/greetings.vue";
import Form from "~/components/form.vue";
export default {
  name: "IndexPage",
  components: { Greetings, Form },
  methods: {
    goTo(id) {
      document.getElementById(id).scrollIntoView({
        behavior: "smooth",
        duration: 400,
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.test {
  width: 100%;
  height: 100vh;
  background-color: aqua;
}
</style>
