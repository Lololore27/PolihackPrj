<template>
  <v-container class="text-center my-12">
    <!-- Main Button -->
    <v-btn color="purple-lighten-2" large @click="dialog = true">
      Post Something
    </v-btn>

    <!-- Feed -->
    <v-container>
      <v-card
        v-for="(post, index) in feed"
        :key="index"
        class="my-4"
        outlined
        style="border: 2px solid #6200ea; text-align: left;"
      >
        <v-card-title>{{ post.title }}</v-card-title>
        <v-card-text>{{ post.content }}</v-card-text>
        <v-card-text class="text-caption">
          <span
            v-for="(tag, i) in post.tags"
            :key="i"
            style="margin-right: 8px; color: #6200ea; font-weight: bold;"
          >
            #{{ tag }}
          </span>
        </v-card-text>
      </v-card>
    </v-container>

    <!-- Dialog -->
    <v-dialog v-model="dialog" max-width="800px">
      <v-card>
        <!-- Toolbar -->
        <v-toolbar
          color="purple-lighten-2"
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
              v-model="newPost.title"
              label="Title"
              variant="filled"
              :rules="[rules.required]"
            ></v-text-field>

            <!-- Content Input -->
            <v-textarea
              v-model="newPost.content"
              label="Text"
              variant="filled"
              :rules="[rules.required]"
            ></v-textarea>

            <!-- Divider -->
            <v-divider class="my-2"></v-divider>

            <!-- Tags -->
            <v-item-group
              multiple
              selected-class="bg-purple"
            >
              <div class="text-caption mb-2">Tags</div>
              <v-item
                v-for="tag in tags"
                :key="tag"
                v-slot="{ selectedClass, toggle }"
              >
                <v-chip
                  :class="selectedClass"
                  @click="toggleTag(tag)"
                >
                  {{ tag }}
                </v-chip>
              </v-item>
            </v-item-group>
          </v-form>
        </v-card-text>

        <!-- Actions -->
        <v-divider></v-divider>
        <v-card-actions>
          <v-btn
            color="success"
            large
            @click="addNewPost"
          >
            Post
          </v-btn>
          <v-btn text color="grey" class="ml-auto" @click="dialog = false">
            Cancel
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
      feed: [], // Array to store posts
      newPost: {
        title: "",
        content: "",
        tags: [],
      },
      selectedTags: [], // Array to hold selected tag strings
      tags: ["Technology", "Health", "Science", "Education", "Sports", "Travel", "Food", "Lifestyle"], // Available tags
      formValid: false,
      rules: {
        required: (value) => !!value || "This field is required.",
      },
    };
  },
  methods: {
    toggleTag(tag) {
      // Toggle tag selection
      const index = this.selectedTags.indexOf(tag);
      if (index === -1) {
        this.selectedTags.push(tag);
      } else {
        this.selectedTags.splice(index, 1);
      }
    },
    addNewPost() {
      // Add a new post to the feed
      if (this.newPost.title && this.newPost.content) {
        this.feed.unshift({
          title: this.newPost.title,
          content: this.newPost.content,
          tags: [...this.selectedTags], // Add selected tags
        });
        // Reset the form and close the dialog
        this.newPost.title = "";
        this.newPost.content = "";
        this.selectedTags = [];
        this.dialog = false;
      } else {
        alert("Please fill out both the title and content fields.");
      }
    },
  },
};
</script>

<style scoped>
.text-caption {
  font-size: 0.8rem;
  font-weight: bold;
}

/* Add padding to the post cards */
.v-card {
  padding: 16px;
  margin: 8px 0;
}

/* Ensure text and elements align to the left */
.v-card-title,
.v-card-text {
  text-align: left;
}
</style>
