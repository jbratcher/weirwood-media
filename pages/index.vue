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
              <v-btn color="white" outlined>View Our Portfolio</v-btn>
            </v-img>
          </v-card>
        </section>

        <!-- Client List Section -->
        <v-container id="clients">
          <h2 class="text-light text-center">Look At All Our Clients</h2>
          <v-sheet>
            <v-slide-group v-model="sliderModel" class="pa-4" center-active show-arrows>
              <v-slide-item v-for="n in 9" :key="n" v-slot:default="{ active, toggle }">
                <v-card
                  :color="active ? 'primary' : 'grey lighten-1'"
                  class="ma-4"
                  height="100"
                  width="200"
                  @click="toggle"
                >
                  <v-row class="fill-height" align="start" justify="end">
                    <v-scale-transition>
                      <v-icon v-if="active" class="mt-2 mr-4" color="white" size="24"></v-icon>
                    </v-scale-transition>
                  </v-row>
                </v-card>
              </v-slide-item>
            </v-slide-group>
          </v-sheet>
        </v-container>

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
  data: () => ({
    sliderModel: null
  }),
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
    margin: 0;
  }
  & > .container:nth-child(odd) {
    background-color: #eee;
    margin: 0;
    min-width: 100%;
    padding: 2rem;
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
  position: relative;
  z-index: 1;
}

// client section

#clients {
  min-width: 100%;
  .v-sheet {
    background: none;
  }
}

// benefits section

#benefits {
  background-image: url('/images/background.svg');
  background-size: cover;
  position: relative;

  .gradient-overlay {
    background-color: rgba(0, 0, 0, 0.5);
    height: 100%;
    position: absolute;
    width: 100%;
    z-index: 0;
    top: 0;
    left: 0;
  }
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
  top: 0;
  left: 0;
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
    font-size: 3rem;
  }
  .v-card__title {
    font-size: 5rem;
  }
  .v-card__subtitle {
    font-size: 2.5rem;
  }
  .grid-3-1 {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    justify-content: space-evenly;
    max-width: 100%;

    & > .v-card {
      margin-bottom: unset;
      margin: 0 2rem;

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
