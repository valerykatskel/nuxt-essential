<template>
  <section>
    <h1>{{ pageTitle }}</h1>
    <ul>
      <li v-for="user in users" :key="user.id">
        <a href="#" @click.prevent="openUser(user)">{{ user.name }}</a>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  // for SSR
  async asyncData({ $axios }) {
    const users = await $axios.$get(
      "https://jsonplaceholder.typicode.com/users"
    );
    return { users };
  },

  data: () => ({
    pageTitle: "Users page"
  }),
  methods: {
    openUser(user) {
      this.$router.push(`/users/${user.id}`);
    }
  }
};
</script>