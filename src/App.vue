<template>
  <v-app id="app">
    <v-container>
      <br>
      <h1 class="text-center"><span class="display-2 red--text">C</span>OVID -19</h1>
      <Total />
      
      <div class="credit text-center">
        <p>COVID-19 Global Data Serving data from John Hopkins University CSSE as a JSON API </p>
          <v-btn color="primary" target="blank"
            href="https://github.com/ratul16/covid-19-info-chart"> 
            <v-icon>mdi-vuetify</v-icon> Repo Link
          </v-btn>
      </div>
      

      <DataTable />
    </v-container>
  </v-app>
</template>

<script>
import DataTable from "./components/DataTable";
import Total from "./components/Total";

export default {
  name: "App",
  components: {
    DataTable,
    Total,
  },
  created() {
    this.$vuetify.theme.dark = true;
  },
};
</script>

<style scoped>

.credit {
  margin-top: 2%;
}

</style>
