<template>
  <v-container>
    <v-card :shaped="true">
      <v-card-title>
        Riwayat Transaksi
      </v-card-title>
      <v-data-table
        :headers="headers"
        :items="transaksi"
        :items-per-page="10"
        sort-by="Tanggal"
        class="elevation-10"
        loading-text="sedang memuat..."
      >
        <!-- <template v-slot:item.Tanggal="{ item }">
              <v-chip color="#3bd6c6" dark outlined>
                  {{ item.Tanggal }}
              </v-chip>
            </template> -->
        <template v-slot:item.JenisTransaksi="{ item }">
          <v-chip :color="getColor(item.JenisTransaksi)" dark>
            {{ item.JenisTransaksi }}
          </v-chip>
        </template>
      </v-data-table>
    </v-card>
  </v-container>
</template>

<script>
import axios from "axios";
import moment from "moment";
export default {
  name: "DataTransaksi",

  data: () => ({
    headers: [
      {
        text: "no.kwt",
        align: "start",
        groupable: false,
        sortable: true,
        value: "TxnID"
      },
      { text: "Bulan", value: "Tanggal" },
      { text: "Jumlah", value: "Amount", sortable: false, groupable: false },
      { text: "Tipe", value: "JenisTransaksi" },
      { text: "Rinci", value: "Description", groupable: false }
    ],
    transaksi: []
  }),

  methods: {
    getColor(JenisTransaksi) {
      if (JenisTransaksi == "debit") return "red";
      else if (JenisTransaksi == "kredit") return "green";
    }
  },

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
          element.Tanggal = moment(element.Tanggal).format("MMMM");

          if (element.JenisTransaksi == 0) {
            element.JenisTransaksi = "kredit";
          }

          if (element.JenisTransaksi == 1) {
            element.JenisTransaksi = "debit";
          }
        });
        this.transaksi = result.data;
      })
      .catch(err => {
        alert(err);
      });
  }
};
</script>
