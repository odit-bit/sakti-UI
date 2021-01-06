<template>
  <v-app>
    <Graph value=bokep />
    <DataTransaksi />
  </v-app>
    <!-- <img alt="Vue logo" src="../assets/logo.png" /> -->
   
</template>

<script>
// @ is an alias to /src
import DataTransaksi from "@/components/DataTransaksi.vue";
import Graph from '../components/Graph.vue';

export default {
  // name: "Transaksi",
  components: {
    DataTransaksi,
    Graph,
  },
  data:() => ({
    //
  }),
};
</script>
