<template>
  <v-container>
    <v-row justify="center" align="center">
      <!-- Main Card Container -->
      <v-col cols="12" md="8">
        <v-card class="bg-deep-purple-lighten-2">
          <v-card-title class="bg-deep-purple-lighten-2 text-h5 text-center"
            >Please share one thing you've <br />
            done recently and you've enjoyed</v-card-title
          >
          <v-card-text>
            
            <!-- Textarea for input -->
            <v-textarea
              v-model="message"
              label="Your message"
              outlined
              rows="4"
              class="mb-4"
            ></v-textarea>

            <!-- Big Text for the question -->
            <v-card-title
              class="bg-deep-purple-lighten-2 text-h5 text-center mb-4"
              >What would you like to do?</v-card-title
            >

            <!-- Radio buttons for options -->
            <v-radio-group v-model="selectedOption" column>
              <v-radio
                label="Practice one of my hobbies"
                value="option_one"
              ></v-radio>
              <v-radio label="Try something new" value="option_two"></v-radio>
              <v-radio
                label="Ask CosticaAi for ideas"
                value="option_three "
              ></v-radio>
            </v-radio-group>

            <!-- Send Button -->
            <v-btn @click="sendMessage" color="deep-purple-lighten-3" block
              >Send</v-btn
            >
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    URL: "http://localhost:8080/user/task";
    return {
      message: "", // Holds the value of the message input
      selectedOption: "", // Holds the selected radio option
    };
  },
  watch: {
    selectedOption(newSelectedOption) {
      this.$emit("option-changed", this.selectedOption);
    }
  },
  methods: {
    async sendMessage() {
      if (this.message.trim() && this.selectedOption) {
        // Here, you can process the message and selected option, e.g., send them to an API
        try {
          const response = await fetch(this.URL, {
            method: "POST",
            headers: {
              "Content-Type": "application/json",
            },
            body: JSON.stringify({
              quote: this.message
            }),
          });
          console.log(response);
        } catch (err) {
          alert(err);
        }
        this.message = ""; // Clear the message input
        this.selectedOption = ""; // Clear the selected optio
      } else {
        alert("Please fill out both the message and select an option!");
      }
    },
  },
};
</script>

<style scoped>
.v-card {
  padding: 20px;
}
</style>
