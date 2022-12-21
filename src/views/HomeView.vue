<template>
  <div class="sc-home-container">
    <v-card-title>
      <span class="text-h2 text-center">Başlık 1</span>
    </v-card-title>
    <v-row class="ma-0" justify="center">
      <v-dialog v-model="dialog" class="sc-dialog">
        <template v-slot:activator="{ on, attrs }">
          <div class="sc-content">
            <v-card
              v-for="(item, index) in contentData"
              :key="index.title"
              class="ma-3 sc-card"
              v-bind="attrs"
              v-on="on"
              @click="selectContent(item)"
            >
              <v-img height="250" class="sc-card-img" :src="item.url"></v-img>
              <v-card-title>{{ item.title }}</v-card-title>
              <v-card-text>
                <!-- <v-row align="center" class="mx-0 mb-1">
          <v-rating
            :value="item.rating"
            color="amber"
            dense
            half-increments
            readonly
            size="14"
          ></v-rating>
          <div class="grey--text">{{ item.rating }} ({{ item.totalRate }})</div>
        </v-row> -->
                <div class="sc-card-desc">
                  {{ item.desc }}
                </div>
              </v-card-text>
            </v-card>
          </div>
        </template>
        <v-card class="sc-dialog-card" scrollable>
          <v-img class="sc-dialog-img" :src="selectedContent.url"></v-img>
          <v-card-title>
            <span class="text-h5">{{ selectedContent.title }}</span>
          </v-card-title>
          <v-card-text class="sc-dialog-desc">
            {{ selectedContent.desc }}
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="green darken-1" text @click="dialog = false">
              Kapat
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},
  data: () => ({
    // windowWidth = window.innerWidth,
    dialog: false,
    contentData: [
      {
        url: "https://m.media-amazon.com/images/I/81-FabsEArL._AC_SL1500_.jpg",
        title: "Proplan Kedi Maması1",
        rating: 1.5,
        totalRate: 34,
        desc: "Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle.",
      },
      {
        url: "https://m.media-amazon.com/images/I/81-FabsEArL._AC_SL1500_.jpg",
        title: "Proplan Kedi Maması2",
        rating: 3.5,
        totalRate: 34,
        desc: "Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. ",
      },
      {
        url: "https://m.media-amazon.com/images/I/81-FabsEArL._AC_SL1500_.jpg",
        title: "Proplan Kedi Maması3",
        rating: 3.5,
        totalRate: 34,
        desc: "Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. ",
      },
      {
        url: "https://m.media-amazon.com/images/I/81-FabsEArL._AC_SL1500_.jpg",
        title: "Proplan Kedi Maması4",
        rating: 3.5,
        totalRate: 34,
        desc: "Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. ",
      },
      {
        url: "https://m.media-amazon.com/images/I/81-FabsEArL._AC_SL1500_.jpg",
        title: "Proplan Kedi Maması5",
        rating: 3.5,
        totalRate: 34,
        desc: "Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. ",
      },
      {
        url: "https://m.media-amazon.com/images/I/81-FabsEArL._AC_SL1500_.jpg",
        title: "Proplan Kedi Maması6",
        rating: 3.5,
        totalRate: 34,
        desc: "Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle. Örnek bir cümle 7. Örnek bir cümle. ",
      },
    ],
    selectedContent: {
      url: "",
      title: "",
      desc: "",
    },
  }),
  methods: {
    selectContent(item) {
      this.selectedContent = {
        url: item.url,
        title: item.title,
        desc: item.desc,
      };
      console.log("for:", item);
    },
  },
};
</script>
<style lang="scss">
.sc-home-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.sc-content {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
}
.v-dialog {
  width: 700px !important;
  display: flex;
  max-height: 80% !important;
}

.sc-card {
  display: flex !important;
  flex-wrap: wrap !important;
  width: 300px !important;
  max-width: 88% !important;
  justify-content: center;
  text-align: center;
}
.sc-card-img {
  width: 100% !important;
  .v-image__image--cover {
    background-size: contain !important ;
  }
}
.sc-dialog-img {
  width: 350px;
}
.sc-card-desc {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 100%;
}
.sc-dialog-card {
  display: flex;
  padding: 16px;
  height: 100%;
  align-items: center;
  flex-direction: column;
}
.sc-dialog-desc {
  padding: 0px 30px;
  font-size: 16px;
}
</style>
