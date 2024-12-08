<template>
  <v-container>
    <div align="center">
      <h2>Costica.Ai</h2>
      <form @submit.prevent="handleSubmit">
        <div>
          <label for="prompt">Prompt: </label>
          <input type="text" id="prompt" v-model="prompt" required />
        </div>
        <h2>{{ costica }}</h2>
        <button type="submit" @click="sendMessage()">Submit</button><br />
        <button @click="this.$router.push({path:'/PublicSpace'})">FORUM</button>
      </form>
    </div>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      marker: false,
      prompt: null,
      icon: "mdi-email",
      URL: "http://localhost:8080/ai",
      costica: null,
      respo: null,
    };
  },
  methods: {
    async sendMessage() {
      console.log(this.prompt);
      try {
        // POST request to the API endpoint
        const response = await fetch(this.URL, {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify({
            prompt: this.prompt,
          }),
        });
        const body = await response.json();
        console.log("wtf", body);

        this.costica = body.choices[0].message.content
        console.log(this.costica)
      } catch (err) {
        alert(err);
      }
    },
    toggleMarker() {
      this.marker = !this.marker;
    },
    clearMessage() {
      this.message = "";
    },
    changeIcon() {
      this.icon = this.icon === "mdi-email" ? "mdi-account" : "mdi-email";
    },
  },
};
</script>

<style>
.fill-height {
  height: 100vh;
}
</style>
