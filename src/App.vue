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
          <router-view :database="users" :windowSize="window" />
        </v-sheet>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Vuetify from "./plugins/vuetify";
import usersData from "./db.json";

export default {
  name: "App",
  components: {},
  data: () => ({
    users: usersData,
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
    this.users[0].url="https://i.pinimg.com/originals/be/a3/72/bea372e98e82e4f2d81e4982361e2654.png"
    // console.log("mockobje: ",this.users)
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
.container {
  margin-top: 20px !important;
}
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
