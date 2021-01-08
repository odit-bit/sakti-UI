<template>
    <v-container>
        <v-card class="mt-4 mx-auto text-center " :shaped="true" >
            <v-card-text >
                Angka Komulatif Kel.Jaticempaka
            </v-card-text>

            <v-divider></v-divider>
            
            <v-row dense>
                <v-col v-for="data in dataCovid" :key="data" >
                    <v-card class="elevation-0 grey lighten-5" >
                        <v-card-subtitle class="black--text">
                           <p>{{data.status}}</p> 
                        </v-card-subtitle>
                        <v-spacer></v-spacer>
                        <v-card-text class="">
                            <!-- <v-chip color="teal" dark outlined> -->
                              <h1 class="font-weight-bold grey--text">{{data.jumlah}}</h1>  
                            <!-- </v-chip> -->
                        </v-card-text>
                    </v-card>
                </v-col>
            </v-row>

            <v-card-text class="text--disabled">
                sumber:{{sumberURL}}
            </v-card-text>

        </v-card>
            
            

    </v-container>
</template>

<script>
import axios from "axios";
export default {
  name: "Covid",

  components: {},

  data() {
    return {
        dataCovid: [],
        sumberURL:"https://covid19-public.digitalservice.id/api/v1/",
    };
  },

  mounted() {
    axios
      .get("https://covid19-public.digitalservice.id/api/v1/sebaran_app_v2/jabar?kode_kab=3275")
      .then(response => {
          let data1 = {
              status : "Suspek",
              jumlah :0
          }
          let data2 = {
              status : "Konfirmasi",
              jumlah :0
          }
          let data3 = {
              status : "Probable",
              jumlah :0
          }
          //assign value for tanggalUpdate  
        //   this.tanggalUpdate = response.data.data.metadata.last_update

          //directive 
          response.data.data.content.forEach(element => {
            if (element.kode_kel == "3275010011"  ) {
                if (element.status == "SUSPECT") {             
                    data1.jumlah += 1
                }
                if (element.status == "CONFIRMATION" ) {                 
                    data2.jumlah += 1
                }
                if (element.status == "PROBABLE") {            
                    data3.jumlah += 1 
                }
            }
          });
        //push to array
        this.dataCovid.push(data1)
        this.dataCovid.push(data2)
        this.dataCovid.push(data3)
      })
      .catch(error => {
        alert(error);
      });
  }
};
</script>
