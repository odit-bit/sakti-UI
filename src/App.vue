<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <!--  -->
    </v-navigation-drawer>

    <v-app-bar app color="teal">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Application</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <v-container>
        <Transaksi />
      </v-container>
    </v-main>

    <v-footer app padless color="teal">
      <v-col class="text-center" cols="12">
        {{ new Date().getFullYear() }} — <strong>Jaticempaka-11</strong>
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>
import Transaksi from "./views/Transaksi";

export default {
  name: "App",

  components: {
    Transaksi
  },

  data: () => ({
    drawer: null
  })
};
</script>
