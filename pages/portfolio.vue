<template>
  <v-layout>
    <v-col>
      <v-container id="portfolio-page">
        <h1>Coming Soon</h1>
        <p>
          Checkout out my work on
          <a
            class="black--text"
            href="https://www.github.com/jbratcher"
          >Github</a>
        </p>
      </v-container>
    </v-col>
  </v-layout>
</template>

<script>
export default {};
</script>

<style lang="scss">
.portfolio-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  p {
    margin: 2rem 0;
  }
}
</style>