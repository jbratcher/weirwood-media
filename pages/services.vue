<template>
  <main>
    <!-- Benefits Section -->
    <v-container id="benefits">
      <v-row>
        <v-col class="text-center">
          <h2 class="text-light white--text">Services</h2>
        </v-col>
      </v-row>
      <v-row>
        <section class="gradient-overlay"></section>
        <v-container class="grid-3-1">
          <v-card>
            <v-icon class="benefits-icon" color="secondary lighten-2">mdi-toolbox-outline</v-icon>
            <v-card-title>Application Development</v-card-title>
            <v-card-text>Have a great idea but not sure how to implement it? Let us show you all the modern options available and what is the best fit for your use case.</v-card-text>
          </v-card>
          <v-card>
            <v-icon class="benefits-icon" color="secondary">mdi-email-send</v-icon>
            <v-card-title>Web Development</v-card-title>
            <v-card-text>Get your idea online and portable. Our solutions cater to exactly what you need depending on what you want. Let us create universal, fast website or application for you.</v-card-text>
          </v-card>
          <v-card>
            <v-icon class="benefits-icon" color="secondary darken-2">mdi-account-supervisor</v-icon>
            <v-card-title>Social Media Integration</v-card-title>
            <v-card-text>Make your internet presence known and stand out with our social media management service.</v-card-text>
          </v-card>
        </v-container>
      </v-row>
    </v-container>
  </main>
</template>

<script>
export default {
  name: 'Services'
};
</script>

<style lang="scss">
</style>