<template>
  <div>
    <v-form name="contact" method="POST" data-netlify="true" lazy-validation>
      <v-text-field
              v-show="false"
              name="form-name"
              value="contact"
      />
      <v-text-field
              :counter="10"
              label="Name"
              name="name"
              required
      ></v-text-field>

      <v-text-field
              label="E-mail"
              name="message"
              required
      ></v-text-field>
      <div data-netlify-recaptcha="true"></div>
      <v-btn block color="secondary" dark type="submit">Send</v-btn>
    </v-form>
  </div>
</template>
