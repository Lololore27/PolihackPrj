<template>
  <v-container>
    <v-card class="mx-auto px-6 py-8" max-width="344">
      <h2 class="align-center">Welcome Back</h2>
      <v-form v-model="form" @submit.prevent="onSubmit">
        <v-text-field
          v-model="username"
          :readonly="loading"
          :rules="[required]"
          class="mb-2"
          label="Username"
          clearable
          prepend-inner-icon="mdi-account-outline"
        ></v-text-field>

        <v-text-field
          :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="visible ? 'text' : 'password'"
          @click:append-inner="visible = !visible"
          v-model="password"
          :readonly="loading"
          :rules="[required]"
          label="Password"
          placeholder="Enter your password"
          clearable
          prepend-inner-icon="mdi-lock-outline"
        ></v-text-field>

        <br />

        <v-btn
          :disabled="!form"
          :loading="loading"
          color="success"
          size="large"
          type="submit"
          variant="elevated"
          block
        >
          Sign In
        </v-btn>
        <v-card-text class="text-center">
          <a
            class="text-blue text-decoration-none"
            href=""
            rel="noopener noreferrer"
            target="_blank"
          >
            Sign up now <v-icon icon="mdi-chevron-right"></v-icon>
          </a>
        </v-card-text>
      </v-form>
    </v-card>
  </v-container>
</template>
<script>
export default {
  data: () => ({
    form: false,
    username: null,
    password: null,
    loading: false,
    visible: false,
  }),

  methods: {
    async onSubmit() {
      // Ensure the form is valid before proceeding
      if (!this.form) {
        return;
      }
      const urlLogin = "http://localhost:8080/users/login";
      console.log(urlLogin);
      this.loading = true; // Show loading spinner
      // Create the data payload to send
      const payload = {
        username: this.username,
        password: this.password,
      };
      console.log(payload);

      // POST request to the API endpoint
      const response = await fetch(urlLogin, {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(payload),
      });
      console.warn(response)
      if(true){
        this.$router.push({path:"/PaginaMain"})
      }
    },
    required(v) {
      return !!v || "Field is required";
    },
  },
};
</script>
