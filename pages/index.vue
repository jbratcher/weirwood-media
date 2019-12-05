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
              <h2 class="text-center white--text">Web Design &amp; Development That Delivers</h2>
              <p class="text-center white--text">Let's make your ideas a reality.</p>
            </v-sheet>
            <v-btn nuxt to="/portfolio" color="white" outlined>View Our Portfolio</v-btn>
          </v-img>
        </v-container>

        <!-- About Section -->
        <v-container id="about">
          <section class="gradient-overlay"></section>
          <h2 class="text-center white--text">Crafting user-optimized software is our passion</h2>
          <p
            class="text-center white--text"
          >We understand people and how they interact with screens.</p>
          <p
            class="white--text"
          >Our process builds blazingly fast, modern apps with user experience in mind from the ground up. We care about delivering cutting-edge, quality work.</p>
        </v-container>

        <!-- Benefits Section -->
        <v-container id="benefits">
          <v-row>
            <v-col class="text-center">
              <h2>Services</h2>
            </v-col>
          </v-row>
          <v-row>
            <v-container class="grid-3-1">
              <v-hover>
                <template v-slot="{ hover }">
                  <v-card :elevation="hover ? 24 : 6">
                    <v-icon class="benefits-icon" color="secondary lighten-2">mdi-toolbox-outline</v-icon>
                    <v-card-title>App Development</v-card-title>
                    <v-card-text>Have a great idea but not sure how to implement it? Let us show you all the modern options available and what is the best fit for your use case.</v-card-text>
                  </v-card>
                </template>
              </v-hover>
              <v-hover>
                <template v-slot="{ hover }">
                  <v-card :elevation="hover ? 24 : 6">
                    <v-icon class="benefits-icon" color="secondary">mdi-email-send</v-icon>
                    <v-card-title>Web Development</v-card-title>
                    <v-card-text>Get your idea online and portable. Our solutions cater to exactly what you need depending on what you want. Let us create universal, fast website or app for you.</v-card-text>
                  </v-card>
                </template>
              </v-hover>
              <v-hover>
                <template v-slot="{ hover }">
                  <v-card :elevation="hover ? 24 : 6">
                    <v-icon class="benefits-icon" color="secondary darken-2">mdi-account-supervisor</v-icon>
                    <v-card-title>Social Media Integration</v-card-title>
                    <v-card-text>Make your internet presence known and stand out with our social media management service.</v-card-text>
                  </v-card>
                </template>
              </v-hover>
            </v-container>
          </v-row>
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
</style>
