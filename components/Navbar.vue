<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand href="#">Vue SSr</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <nuxt-link exact no-prefetch active-class="active" class="nav-link" to="/">Home</nuxt-link>

          <nuxt-link no-prefetch active-class="active" class="nav-link" to="/about">About</nuxt-link>
          <nuxt-link no-prefetch active-class="active" class="nav-link" to="/users">Users</nuxt-link>

          <nuxt-link
            v-if="!hasToken"
            no-prefetch
            active-class="active"
            class="nav-link"
            to="/login"
          >Login</nuxt-link>

          <li v-else class="nav-item">
            <a @click.prevent="logout" class="nav-link" href>Logout</a>
          </li>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {
  methods: {
    logout() {
      this.$store.dispatch("logout");
      this.$router.push("/login");
    }
  },
  computed: {
    hasToken() {
      return this.$store.getters.hasToken;
    }
  }
};
</script>