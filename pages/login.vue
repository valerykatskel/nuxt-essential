<template>
  <section>
    <h1>Login page</h1>
    <b-alert v-if="$route.query.message" variant="danger" show>Need login first!</b-alert>

    <b-form @submit.prevent="onSubmit">
      <b-form-group
        id="input-group-1"
        label="Email address:"
        label-for="input-1"
        description="We'll never share your email with anyone else."
      >
        <b-form-input id="input-1" type="email" placeholder="Enter email"></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Login</b-button>
    </b-form>
    <nuxt-link to="/">To home page</nuxt-link>
  </section>
</template>

<script>
export default {
  layout: "empty",
  methods: {
    onSubmit() {
      this.$store.dispatch("login");
      this.$router.push("/");
    }
  }
};
</script>

<style scoped>
section {
  margin: 0 auto;
  width: 500px;
}
</style>