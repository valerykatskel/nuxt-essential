<template>
  <div>
    <Navbar />

    <main>
      <b-container>
        <Nuxt />
      </b-container>
    </main>
  </div>
</template>

<script>
import NavBar from "@/components/Navbar";
export default {
  components: {
    NavBar
  }
};
</script>

<style>
</style>
