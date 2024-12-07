<template>
    <v-container class="text-center my-12">
      <!-- Main Button -->
      <v-btn block color="deep-purple-accent-1" size="x-large" @click="dialog = true">
        Post Something
      </v-btn>
  
      <!-- Dialog -->
      <v-dialog v-model="dialog" max-width="800px">
        <v-card>
          <!-- Toolbar -->
          <v-toolbar
            color="deep-purple-lighten-1"
            dark
            flat
          >
            <v-toolbar-title>Submit a Post</v-toolbar-title>
          </v-toolbar>
  
          <!-- Card Content -->
          <v-card-text>
            <v-form ref="form" v-model="formValid">
              <!-- Title Input -->
              <v-text-field
                v-model="post.title"
                label="Title"
                variant="filled"
                :rules="[rules.required]"
              ></v-text-field>
  
              <!-- Content Input -->
              <v-textarea
                v-model="post.content"
                label="Text"
                variant="filled"
                :rules="[rules.required]"
              ></v-textarea>
  
              <!-- Divider -->
              <v-divider class="my-2"></v-divider>
  
              <!-- Tags -->
              <v-item-group selected-class="bg-purple" multiple>
                <div class="text-caption mb-2">Tags</div>
                <v-item
                  v-for="n in 8"
                  :key="n"
                  v-slot="{ selectedClass, toggle }"
                >
                  <v-chip
                    :class="selectedClass"
                    @click="toggle"
                  >
                    Tag {{ n }}
                  </v-chip>
                </v-item>
              </v-item-group>
            </v-form>
          </v-card-text>
  
          <!-- Actions -->
          <v-divider></v-divider>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn text color="grey" @click="dialog = false">
              Cancel
            </v-btn>
            <v-btn
              color="success"
              :disabled="!formValid"
              @click="submitPost"
            >
              Post
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-container>
  </template>
  
  <script>
  export default {
    data() {
      return {
        dialog: false,
        post: {
          title: "",
          content: "",
        },
        formValid: false,
        rules: {
          required: (value) => !!value || "This field is required.",
        },
      };
    },
    methods: {
      submitPost() {
        // Handle form submission
        alert(`Title: ${this.post.title}\nContent: ${this.post.content}`);
        this.dialog = false; // Close the dialog
        // Clear the form
        this.post.title = "";
        this.post.content = "";
      },
    },
  };
  </script>
  
  <style scoped>
  .text-caption {
    font-size: 0.8rem;
    font-weight: bold;
  }
  </style>
  