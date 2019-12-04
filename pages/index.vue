<template>
  <v-layout>
    <v-flex>
      <main>
        <!-- Hero Section -->
        <v-container id="hero" class="pa-0">
          <v-img
            class="white--text align-center"
            alt="hero description"
            height="400px"
            src="/images/hero-md.jpg"
            lazy-src="https://picsum.photos/1280/720"
            srcset="/images/hero-lg.jpg 768w, /images/hero-xl.jpg 1024w"
            cover
          >
            <section class="gradient-overlay"></section>
            <v-sheet class="image-text">
              <h2 class="text-center white--text">Web &amp; App Development</h2>
              <p class="text-center white--text">Let's make your ideas a reality.</p>
            </v-sheet>
            <v-btn color="white" outlined>View Our Portfolio</v-btn>
          </v-img>
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
                <v-icon class="benefits-icon" color="secondary lighten-2">mdi-toolbox-outline</v-icon>
                <v-card-title>App Development</v-card-title>
                <v-card-text>Have a great idea but not sure how to implement it? Let us show you all the modern options available and what is the best fit for your use case.</v-card-text>
              </v-card>
              <v-card>
                <v-icon class="benefits-icon" color="secondary">mdi-email-send</v-icon>
                <v-card-title>Web Development</v-card-title>
                <v-card-text>Get your idea online and portable. Our solutions cater to exactly what you need depending on what you want. Let us create universal, fast website or app for you.</v-card-text>
              </v-card>
              <v-card>
                <v-icon class="benefits-icon" color="secondary darken-2">mdi-account-supervisor</v-icon>
                <v-card-title>Social Media Integration</v-card-title>
                <v-card-text>Make your internet presence known and stand out with our social media management service.</v-card-text>
              </v-card>
            </v-container>
          </v-row>
        </v-container>

        <!-- About Section -->
        <v-container id="about">
          <h2 class="text-center">Crafting user-optimized software is our passion</h2>
          <p class="text-center">We care about delivering cutting-edge, quality work</p>
          <p
            class="px-12"
          >We understand people and how they interact with screens. Our process builds blazingly fast, modern apps with user experience in mind from the ground up.</p>
        </v-container>

        <!-- Contact Section -->
        <v-container id="contact">
          <section class="gradient-overlay"></section>
          <h2 class="text-center white--text">Let Us Help With Your Next Project</h2>
          <p class="text-center white--text mt-5">Drop us a line!</p>
          <v-form
            ref="form"
            v-model="valid"
            name="contact"
            method="post"
            value="contactform"
            data-netlify="true"
            lazy-validation
          >
            <v-text-field
              class="white--text"
              v-model="name"
              :rules="nameRules"
              label="Name"
              name="name"
              required
            ></v-text-field>
            <v-text-field
              class="white--text"
              v-model="email"
              :rules="emailRules"
              label="E-mail"
              name="email"
              required
            ></v-text-field>
            <v-textarea
              class="white--text"
              v-model="message"
              :rules="messageRules"
              label="Your Message"
              name="message"
              required
            ></v-textarea>
            <v-btn color="secondary" class="mr-4" @click="reset">Reset</v-btn>
            <v-btn type="submit" :disabled="!valid" color="primary" class="mr-4">Submit</v-btn>
          </v-form>
        </v-container>
      </main>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data: () => ({
    valid: true,
    name: '',
    nameRules: [v => !!v || 'Name is required'],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+\..+/.test(v) || 'E-mail must be valid'
    ],
    message: '',
    messageRules: [
      v => !!v || 'Message is required',
      v =>
        (v && v.length <= 1000) ||
        'Your message must be less than 1000 characters. Please email us at company@email.com'
    ]
  }),
  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        this.snackbar = true;
      }
    },
    reset() {
      this.$refs.form.reset();
      this.$refs.form.resetValidation();
    }
  },
  head() {
    return {
      script: [
        { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }
      ]
    };
  }
};
</script>

<style lang="scss">
h2 {
  font-size: 2.33rem;
  font-weight: 700;
  position: relative;
  z-index: 1;
}

.image-text p {
  font-size: 1.75rem;
}

// sections

.container {
  min-height: 400px;
  min-width: 100%;
  padding: 4rem 0;
}

// hero section

#hero {
  .v-responsive__content {
    align-items: center;
    display: flex;
    flex-direction: column;
    height: 100%;
    justify-content: space-evenly;
    position: relative;
  }
  .v-sheet {
    background: transparent;
  }
}

// benefits section

#benefits {
  background-image: url('/images/background.svg');
  background-size: cover;
  min-width: 100%;
  position: relative;

  .gradient-overlay {
    background-color: rgba(0, 0, 0, 0.3);
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

.v-card__title {
  font-family: 'Libre Franklin', sans-serif;
  font-size: 2.33rem;
  font-weight: 700;
  line-height: 1.125em;
  text-align: center;
  word-break: break-word;
}

.v-card__subtitle {
  font-family: 'Libre Franklin', sans-serif;
  font-size: 1.33rem;
}

a {
  font-weight: bold;
  color: #526488;
}

// contact section

#contact {
  background-image: url('/images/contact-form-background.svg');
  background-size: cover;
  background-position: center;
  min-width: 100%;
  padding: 4rem 0;
  position: relative;

  .gradient-overlay {
    background-color: rgba(255, 255, 255, 0.1);
    height: 100%;
    position: absolute;
    width: 100%;
    z-index: 0;
    top: 0;
    left: 0;
  }

  p:first-of-type {
    position: relative;
  }

  form {
    background: #fff;
    border-radius: 0.25rem;
    padding: 4rem;
    position: relative;
    width: 80vw;
  }
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
    justify-content: space-around;
    justify-content: flex-start;
    margin-bottom: 2rem;
    padding: 1rem 0;
    & > .v-icon {
      font-size: 4rem;
    }
  }
}

@media screen and (min-width: 768px) {
  h2 {
    font-size: 3.5rem;
  }

  .image-text p {
    font-size: 1.75rem;
  }

  // about section

  #about {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    justify-content: space-evenly;
    min-height: 600px;
    padding: 4rem;

    & > * {
      margin: 1rem 0;
    }

    h2 {
      font-size: 3rem;
      font-weight: 700;
      line-height: 1;
    }

    & > p:first-of-type {
      font-size: 1.75rem;
      font-weight: 100;
    }

    p {
      font-size: 1.25rem;
    }
  }

  // Benefits Icons Grid

  .grid-3-1 {
    align-items: stretch;
    display: grid;
    grid-template-columns: repeat(3, 1fr);

    & > .v-card {
      margin-bottom: unset;
      margin: 0 2rem;

      & > .v-icon {
        font-size: 8rem;
      }

      & > .v-card__title {
        font-size: 2rem;
      }

      & > .v-card__text {
        font-size: 1.25rem;
        line-height: 1.5;
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
      background: #fff;
      margin: 4rem auto;
      width: 50vw;
    }
  }
}
</style>
