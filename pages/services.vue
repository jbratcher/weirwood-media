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
            <v-icon class="benefits-icon" color="primary lighten-2">mdi-toolbox-outline</v-icon>
            <v-card-title>1st Service</v-card-title>
            <v-card-text>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</v-card-text>
          </v-card>
          <v-card>
            <v-icon class="benefits-icon" color="primary">mdi-email-send</v-icon>
            <v-card-title>2nd Service</v-card-title>
            <v-card-text>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</v-card-text>
          </v-card>
          <v-card>
            <v-icon class="benefits-icon" color="primary darken-2">mdi-account-supervisor</v-icon>
            <v-card-title>3rd Service</v-card-title>
            <v-card-text>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</v-card-text>
          </v-card>
        </v-container>
      </v-row>
    </v-container>
  </main>
</template>

<script>
export default {
  name: 'Services'
}
</script>

<style lang="scss">
</style>