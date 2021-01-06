<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <!--  -->
    </v-navigation-drawer>

    <v-app-bar app color="transparent">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Application</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <v-container>
        <Transaksi/>
      </v-container>
    </v-main>

    <v-footer app padless color="transparent">
    <v-col
      class="text-center"
      cols="12"
    >
      {{ new Date().getFullYear() }} — <strong>Jaticempaka-11</strong>
    </v-col>
  </v-footer>
  </v-app>
</template>


<script>
import Transaksi from './components/DataTransaksi.vue';



export default {
  name: "App",

  components: {
    Transaksi,
  },

  data: () => ({
    drawer: null
  }),
};
</script>
