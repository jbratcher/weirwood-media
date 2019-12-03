<template>
  <v-layout>
    <v-flex>
      <main>
        <!-- Hero Section -->
        <section id="hero">
          <v-card class="text-center">
            <v-img
              class="white--text align-center"
              alt="hero description"
              height="70vh"
              src="/images/hero-md.jpg"
              lazy-src="https://picsum.photos/1280/720"
              srcset="/images/hero-lg.jpg 768w, /images/hero-xl.jpg 1024w"
              cover
            >
              <section class="gradient-overlay"></section>
              <v-card-title class="text-center">Witty headline</v-card-title>
              <v-card-subtitle
                class="subtitle white--text text-center"
              >A subtitle to expand on the headline.</v-card-subtitle>
            </v-img>
          </v-card>
        </section>

        <!-- Benefits Section -->
        <v-container>
          <v-row id="benefits">
            <v-col class="text-center">
              <h2 class="text-light">Services</h2>
            </v-col>
          </v-row>
          <v-row>
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

        <!-- About Section -->
        <section id="about" class="py-12">
          <h1 class="display-1 pl-12">About Section</h1>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="py-12">
          <h1 class="display-1 pl-12">Contact Section</h1>
        </section>
      </main>
    </v-flex>
  </v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  },
  head() {
    return {
      script: [
        { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }
      ]
    }
  }
}
</script>

<style lang="scss">
main {
  & > section:nth-child(odd) {
    background-color: #eee;
  }
}

#hero {
  .v-responsive__content {
    align-items: center;
    display: flex;
    flex-direction: column;
    height: 100%;
    justify-content: space-evenly;
    position: relative;
    .v-card__title {
      display: flex;
      justify-content: center;
    }
  }
}

// sections

h2 {
  font-size: 2.33rem;
}

.v-card__title {
  font-family: 'Libre Franklin', sans-serif;
  font-size: 2.33rem;
  font-weight: 700;
  line-height: 1.125em;
}

.v-card__subtitle {
  font-family: 'Libre Franklin', sans-serif;
  font-size: 1.33rem;
}

a {
  font-weight: bold;
  color: #526488;
}

.gradient-overlay {
  background-image: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.4),
    rgba(0, 0, 0, 0.7)
  );
  height: 100%;
  position: absolute;
  width: 100%;
  z-index: -1;
}

.text-light {
  font-weight: 100;
}

.grid-3-1 {
  display: flex;
  flex-direction: column;
  max-width: 85vw;
  & > .v-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-bottom: 2rem;
    padding: 1rem 0;
    & > .v-icon {
      font-size: 4rem;
    }
  }
}

@media screen and (min-width: 768px) {
  h2 {
    font-size: 4rem;
  }
  .v-card__title {
    font-size: 5rem;
  }
  .v-card__subtitle {
    font-size: 2.5rem;
  }
  .grid-3-1 {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
    max-width: 100%;

    & > .v-card {
      margin-bottom: unset;

      & > .v-icon {
        font-size: 8rem;
      }

      & > .v-card__title {
        font-size: 2rem;
      }
    }
  }
}
</style>
