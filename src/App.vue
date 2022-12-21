<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app v-if="menuVersion > window.width">
      <div class="sc-side-nav">
        <v-btn
          class="my-3"
          v-for="item in items"
          :key="item.title"
          link
          :to="item.to"
        >
          <!-- {{ item.title }}  -->
          {{ item.title }}
        </v-btn>
      </div>
    </v-navigation-drawer>

    <v-app-bar app>
      <v-app-bar-nav-icon
        @click="drawer = !drawer"
        v-if="menuVersion > window.width"
      ></v-app-bar-nav-icon>
      <div class="sc-top-nav" v-if="menuVersion <= window.width">
        <v-btn
          class="ml-6"
          v-for="item in items"
          :key="item.title"
          link
          :to="item.to"
        >
          {{ item.title }}
        </v-btn>
      </div>
    </v-app-bar>

    <v-main class="grey lighten-3">
      <v-container>
        <v-sheet min-height="70vh" rounded="lg">
          <router-view />
        </v-sheet>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Vuetify from "./plugins/vuetify";
export default {
  name: "App",
  components: {},
  data: () => ({
    menuVersion: 960,
    window: {
      width: 0,
      height: 0,
    },
    items: [
      {
        title: "Dashboard",
        to: "/",
      },
      {
        title: "About",
        to: "/about",
      },
      {
        title: "Package",
        to: "/package",
      },
      {
        title: "Settings",
        to: "/settings",
      },
    ],
    drawer: null,
  }),
  created() {
    window.addEventListener("resize", this.handleResize);
    this.handleResize();
  },
  computed: {},
  methods: {
    handleResize() {
      this.window.width = window.innerWidth;
      this.window.height = window.innerHeight;
    },
  },
};
</script>
<style lang="scss">
.sc-side-nav {
  display: flex;
  flex-direction: column;
  padding: 30px;
}
.sc-top-nav {
  display: flex;
  width: 100%;
  justify-content: space-evenly;
}
</style>
