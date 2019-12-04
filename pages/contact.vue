<template>
  <main>
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
        <v-btn color="secondary" class="mr-4" @click="reset">Reset</v-btn>
        <v-btn :disabled="!valid" color="primary" class="mr-4" @click="validate">Submit</v-btn>
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
    ],
    select: null,
    items: ['Item 1', 'Item 2', 'Item 3', 'Item 4']
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