<template>
  <div>
    <v-navigation-drawer v-model="drawer" absolute temporary>
      <v-list class="pa-1">
        <v-list-tile avatar>
          <v-list-tile-avatar>
            <img src="https://randomuser.me/api/portraits/men/85.jpg" />
          </v-list-tile-avatar>

          <v-list-tile-content>
            <v-list-tile-title>John Leider</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
      <v-list>
        <v-text-field
          clearable
          flat
          label="Search"
          prepend-inner-icon="search"
          solo
          single-line
          hide-details
        ></v-text-field>
      </v-list>

      <v-list class="pt-0" dense>
        <v-divider></v-divider>

        <v-list-tile v-for="item in items" :key="item.title" :to="item.to">
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>

          <v-list-tile-content>
            <v-list-tile-title>{{ item.title }}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar dark color="primary" clipped-left fixed app>
      <v-toolbar-side-icon
        @click.stop="drawer = !drawer"
        class="hidden-md-and-up"
      ></v-toolbar-side-icon>
      <v-toolbar-title class="headline text-uppercase white--text">
        <span>Vuetify</span>
        <span class="font-weight-light">MATERIAL DESIGN</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-expand-x-transition>
        <v-text-field
          class="hidden-sm-and-down"
          clearable
          flat
          label="Search"
          prepend-inner-icon="search"
          solo-inverted
          single-line
          hide-details
          v-show="showSearchInput"
        ></v-text-field>
      </v-expand-x-transition>

      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn icon @click="showSearchInput = !showSearchInput">
          <v-icon>search</v-icon>
        </v-btn>
        <v-btn flat to="/">Home</v-btn>
        <v-btn flat to="/about">About</v-btn>
      </v-toolbar-items>
    </v-toolbar>
  </div>
</template>

<script>
export default {
  name: "Header",

  data() {
    return {
      drawer: null,
      showSearchInput: false,
      items: [
        { title: "Home", icon: "dashboard", to: "/" },
        { title: "About", icon: "question_answer", to: "/about" }
      ]
    };
  }
};
</script>
