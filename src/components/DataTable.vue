<template>

  <v-card class="data-table">
    <v-card-title>
      <h2>Covid-19 Information Chart</h2>
      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="Search Countries"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>
    <v-data-table
      :headers="testhead"
      :items="testdata"
      :search="search"
    >

    <template v-slot:item.confirmed="{ item }">
      <v-text class="blue--text text--darken-1">{{item.confirmed}}</v-text>
    </template>

    <template v-slot:item.recovered="{ item }">
      <v-text class="green--text text--darken-1">{{item.recovered}}</v-text>
    </template>

    <template v-slot:item.deaths="{ item }">
      <v-text class="red--text text--darken-3">{{item.deaths}}</v-text>
    </template>

    <template v-slot:item.active="{ item }">
      <v-text class="cyan--text text--darken-1">{{item.active}}</v-text>
    </template>

    <template v-slot:item.incidentRate="{ item }">
      <v-text class="yellow--text text--darken-1">{{(item.incidentRate /100).toFixed(2)}} %</v-text>
    </template>

    <template v-slot:item.provinceState="{ item }">
      <v-chip color="primary" label v-if="item.provinceState != null"> {{item.provinceState}}</v-chip>
    </template>



    </v-data-table>
  </v-card>
  
</template>

<script>

import response from '@/assets/data.json'

  export default {
    data () {
      return {
        search: '',
        headers: [
          {
            text: 'Country Name',
            align: 'start',
            value: 'name',
          },
          { text: 'Total Confirmed', value: 'confirm' },
          { text: 'Total Recovered', value: 'recover' },
          { text: 'Total Deaths', value: 'deaths' },
          { text: 'Active Case', value: 'active' },
          { text: 'Incident Rate', value: 'rate' },
        ],
        testhead:[
            {
            text: 'Country Name',
            align: 'start',
            value: 'countryRegion',
          },
          { text: 'Total Confirmed', value: 'confirmed' },
          { text: 'Total Recovered', value: 'recovered' },
          { text: 'Total Deaths', value: 'deaths' },
          { text: 'Active Case', value: 'active' },
          { text: 'Incident Rate', value: 'incidentRate' },
          { text: 'Province/State', value: 'provinceState' },
        ]
        ,
        testdata:response,
        apiData: [
          {
            name: 'countryRegion',
            confirm: 159,
            recover: 6.0,
            deaths: 24,
            active: 4.0,
            rate: '1%',
            lat:'',
            lon:'',
            iso2:''
          },
        ],
      }
    },
  }
</script>

<style scoped>

.data-table {
  margin-top: 2%;
}
</style>