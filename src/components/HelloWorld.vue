<template>
  <v-card>
    <v-card-title>
      TRANSAKSI
    </v-card-title>
    <v-data-table
        dense
        :headers="headers"
        :items="transaksi"
        :items-per-page="10"
        sort-by="Tanggal"
        group-by="JenisTransaksi"
        show-group-by
        class="elevation-10"
      >
      </v-data-table>
  </v-card>
</template>

<script>
import axios from "axios";
import moment from "moment";
export default {
  name: "HelloWorld",

  data: () => ({
    headers: [
      {
        text: "Txn ID",
        align: "start",
        groupable: false,
        sortable: true,
        value: "TxnID"
      },
      { text: "Bulan/Tahun", value: "Tanggal" },
      { text: "Jumlah", value: "Amount", sortable: false, groupable: false },
      { text: "Code", value: "JenisTransaksi" },
      { text: "Description", value: "Description", groupable: false },
      { text: "Tag", value: "Tag" }
    ],
    transaksi: []
  }),
  mounted() {
    axios
      .get(process.env.VUE_APP_API)
      .then(result => {
        result.data.forEach(element => {
          // element.Amount = element.Amount.toLocaleString("id-ID")
          element.Amount = new Intl.NumberFormat("id-ID", {
            style: "currency",
            currency: "IDR"
          }).format(element.Amount);
          element.Tanggal = moment(element.Tanggal).format("MMM YY");
        });
        this.transaksi = result.data;
        
      })
      .catch(err => {
        alert(err);
      });
  }
};
</script>
