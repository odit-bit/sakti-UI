<template>
  <v-footer padless :absolute="true">
    <v-col class="text-center" cols="12">
      {{ new Date().getFullYear() }} — <strong>Jaticempaka-11</strong>
    </v-col>
  </v-footer>
</template>

<script>
export default {
  data: () => ({
    icons: ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"]
  })
};
</script>
