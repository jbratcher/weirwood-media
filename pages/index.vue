<template>
  <v-layout>
    <v-flex>
      <main>
        <!-- Hero Section -->
        <v-container id="hero" class="pa-0">
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
            <h2 class="text-center">Witty headline</h2>
            <p class="subtitle white--text text-center">A subtitle to expand on the headline.</p>
            <v-btn color="white" outlined>View Our Portfolio</v-btn>
          </v-img>
        </v-container>

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
        <v-container id="about">
          <h2 class="text-center">We are the best at what we do</h2>
          <p class="text-center">We've been doing this since the year we were founded</p>
          <p>My philosophy is basically this, and this is something I live by and I always have and I always will. Don't ever, for any reason, do anything, to anyone, for any reason, ever, no matter what, no matter where, or who, or who you are with, or where you are going, or where you've been, ever, for any reason whatsoever.</p>
        </v-container>

        <!-- Contact Section -->
        <v-container id="contact">
          <h2 class="text-center">Let Us Help With Your Next Project</h2>
          <p class="text-center">Drop us a line</p>
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-text-field v-model="name" :rules="nameRules" label="Name" required></v-text-field>
            <v-text-field v-model="email" :rules="emailRules" label="E-mail" required></v-text-field>
            <v-textarea v-model="message" :rules="messageRules" label="Your Message" required></v-textarea>
            <v-select
              v-model="select"
              :items="items"
              :rules="[v => !!v || 'Item is required']"
              label="Request Type"
              required
            ></v-select>
            <v-btn color="error" class="mr-4" @click="reset">Reset</v-btn>
            <v-btn :disabled="!valid" color="success" class="mr-4" @click="validate">Submit</v-btn>
          </v-form>
        </v-container>
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
    sliderModel: null,
    valid: true,
    name: '',
    nameRules: [v => !!v || 'Name is required'],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+\..+/.test(v) || 'E-mail must be valid'
    ],
    messageRules: [
      v => !!v || 'Message is required',
      v =>
        (v && v.length <= 1000) ||
        'Your message must be less than 1000 characters. Please email us at company@email.com'
    ],
    select: null,
    items: ['Item 1', 'Item 2', 'Item 3', 'Item 4']
  }),
  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        this.snackbar = true
      }
    },
    reset() {
      this.$refs.form.reset()
      this.$refs.form.resetValidation()
    }
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
h2 {
  font-size: 2.33rem;
  font-weight: 700;
  position: relative;
  z-index: 1;
}

p:first-of-type {
  font-weight: 100;
  font-size: 1.5rem;
}

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
  }
}

// sections

.container {
  min-height: 70vh;
}

// client section

#clients {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  justify-content: space-evenly;
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

// about section

#about {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  justify-content: space-evenly;
  padding: 4rem 2rem;
}

#contact {
  padding: 4rem 0;

  form {
    margin: 4rem auto;
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

// Benefit Icons Grid

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
    font-size: 4.5rem;
  }

  p:first-of-type {
    font-size: 2.33rem;
  }

  // about section

  #about {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    justify-content: space-evenly;
    padding: 4rem;
    min-height: 70vh;

    & > * {
      margin: 1rem 0;
    }

    h2 {
      font-size: 4.5rem;
      font-weight: 700;
    }

    & > p:first-of-type {
      font-size: 1.5rem;
      font-weight: 100;
    }
  }

  // Benefits Icons Grid

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

  // contact section

  #contact {
    h2 {
      font-size: 3rem;
      padding: 0 10vw;
    }
    p:first-of-type {
      font-size: 2rem;
    }
    form {
      margin: 4rem auto;
      width: 50vw;
    }
  }
}
</style>
