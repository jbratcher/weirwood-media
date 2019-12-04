<template>
  <main class="about-page">
    <!-- About Section -->
    <v-container>
      <h2 class="text-center">We care about providing cutting-edge, quality work</h2>
      <p class="text-center my-12">Crafting amazing software and web apps is our passion</p>
      <p>We understand people and how they interact with screens. Our process builds blazingly fast, modern applications with user experience in mind from the ground up.</p>
    </v-container>
  </main>
</template>

<script>
export default {
  name: 'About'
};
</script>

<style lang="scss">
main.about-page .container p:first-of-type {
  font-size: 1.25rem;
}
@media screen and (min-width: 768px) {
  main.about-page {
    margin: 0 auto;
    width: 70vw;
    .container {
      p:first-of-type {
        font-size: 1.75rem;
      }
      p {
        font-size: 1.25rem;
      }
    }
  }
}
</style>