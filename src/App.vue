<template>
  <v-app id="inspire" >

    <!-- APP- BAR -->
    <v-app-bar app elevate-on-scroll class="white" >
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>ICON</v-toolbar-title>
    </v-app-bar>

    <!-- nav drawer -->
    <v-navigation-drawer v-model="drawer" fixed temporary>
       <v-list-item>
        <v-list-item-content color="#00B100">
          <v-list-item-title class="title">
            Binalindung
          </v-list-item-title>
          <v-list-item-subtitle>
            Command Center
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon color="#00B100">{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>

          <v-spacer></v-spacer>

        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main >
        <router-view></router-view>
    </v-main>

    <v-footer app padless class="white" elevation="0" >
      <v-col class="text-center" cols="12">
        {{ new Date().getFullYear() }} — Media Informasi <strong>Binalindung Rw.11</strong>
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>

export default {
  name: "App",

  components: {
//
  },

   data () {
      return {
        drawer: null,
        items: [
          { title: 'Keuangan', icon: 'mdi-cash', to: '/transaksi'},
          { title: 'Covid', icon: 'mdi-hospital-box-outline', to : "/covid" },
          { title: 'About', icon: 'mdi-help-box' },
        ],
        right: null,
      }
    },
};
</script>
