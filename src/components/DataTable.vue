<template>

  <v-card class="data-table">
    <v-card-title>
      <h2>Information Chart</h2>
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
      :headers="headers"
      :items="apiData"
      :search="search"
    >

    <template v-slot:item.confirmed="{ item }">
      <span class="blue--text text--darken-1">{{item.confirmed}}</span>
    </template>

    <template v-slot:item.recovered="{ item }">
      <span class="green--text text--darken-1">{{item.recovered}}</span>
    </template>

    <template v-slot:item.deaths="{ item }">
      <span class="red--text text--darken-3">{{item.deaths}}</span>
    </template>

    <template v-slot:item.active="{ item }">
      <span class="cyan--text text--darken-1">{{item.active}}</span>
    </template>

    <template v-slot:item.incidentRate="{ item }">
      <span class="yellow--text text--darken-1">{{(item.incidentRate /100).toFixed(2)}} %</span>
    </template>

    <template v-slot:item.provinceState="{ item }">
      <v-chip color="primary" label v-if="item.provinceState != null"> {{item.provinceState}}</v-chip>
    </template>


    </v-data-table>
  </v-card>
  
</template>

<script>

import axios from 'axios'

  export default {
    data () {
      return {
        search: '',
        headers: [
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
        ],
        apiData:[],
      }
    },
    mounted(){
      this.getData();
    },
    methods:{
      getData(){
          axios.get('https://covid19.mathdro.id/api/confirmed')
          .then(res =>{
            this.apiData =res.data
          })
          .catch(err=>{
            console.error(err);
          })
      }
    }
  }
</script>

<style scoped>

.data-table {
  margin-top: 3%;
}
</style>