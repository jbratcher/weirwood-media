<template>
  <main>
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
</template>

<script>
export default {
  name: 'Contact',
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
  }
};
</script>

<style lang="scss">
</style>