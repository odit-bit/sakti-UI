<template>
  <v-app>
    <v-container>
      <!-- <Graph /> -->
    <v-card :shaped="true" class="mt-4 mx-auto white--text" color="#00B100" >
      
      <v-spacer></v-spacer>

      <v-card-title >
        Riwayat Transaksi
      </v-card-title>

      <DataTransaksi />
      
    </v-card>
  </v-container>
  </v-app>
</template>

<script>
// @ is an alias to /src
import DataTransaksi from "@/components/DataTransaksi.vue";
// import Graph from "../components/Graph.vue";

export default {
  components: {
    DataTransaksi,
    // Graph,
  },
  data: () => ({
    //
  })
};
</script>
