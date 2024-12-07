
  
  <template>
    <div>
      <!-- Bara de navigare -->
      <v-app-bar
        color="purple-darken-2"
        prominent
        absolute
      >
        <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title>You Can Do It!</v-toolbar-title>
  
        <v-spacer></v-spacer>
  
        <template v-if="$vuetify.display.mdAndUp">
      
        </template>
  

      </v-app-bar>
  
      <!-- Drawer -->
      <v-navigation-drawer
        v-model="drawer"
        :location="$vuetify.display.mobile ? 'bottom' : 'left'"
        absolute
        temporary
      >
      <v-list dense>
        <!-- Link Direct pentru Home -->
        <v-list-item
          link
          title="Home"
          to="PaginaMain"
        />
            <!-- Link Direct pentru About -->
        <v-list-item
          link
          title="Our Comunity"
          to="/PublicSpace"
        />

        <!-- Link Direct pentru Contact -->
        <v-list-item
          link
          to="/MySpace"
        >
          <v-list-item-title>My Space </v-list-item-title>
        </v-list-item>
      </v-list>

      </v-navigation-drawer>
    </div>
  </template>
  
  <script>
  export default {
    data: () => ({
      drawer: false,
      items: [
        { title: 'Foo', value: 'foo' },
        { title: 'Bar', value: 'bar' },
        { title: 'Fizz', value: 'fizz' },
        { title: 'Buzz', value: 'buzz' },
      ],
    }),
  };
  </script>
  
  <style scoped>
  /* Stiluri personalizate */
  </style>
  