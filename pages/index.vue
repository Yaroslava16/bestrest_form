<template>
  <div>
    <Greetings />
    <Form />
  </div>
</template>

<script>
import Greetings from "~/components/greetings.vue";
import Form from "~/components/form.vue";
export default {
  name: "IndexPage",
  components: { Greetings, Form },
};
</script>

<style lang="scss" scoped>
.test {
  width: 100%;
  height: 100vh;
  background-color: aqua;
}
</style>
