<template>
<v-card class="topbar">
  <v-row align="center" justify="center">
    
    <v-col sm='12' md="4">
        <h2 class="text-center">Total Confirmed</h2>
        <h1 class="text-center blue--text text--darken-1">{{confirmed}}</h1>

    </v-col>

    <v-col sm='12' md="4">
        <h2 class="text-center">Total Recovered</h2>
        <h1 class="text-center green--text text--darken-1">{{recovered}}</h1>
    </v-col>

    <v-col sm='12' md="4">
        <h2 class="text-center">Total Death</h2>
        <h1 class="text-center red--text text--darken-3">{{deaths}}</h1>
    </v-col>
  </v-row>
</v-card>
</template>

<script>
import axios from 'axios'

export default {

  data(){
    return {
      confirmed:0,
      recovered:0,
      deaths:0,
    }
  },
  mounted(){
    this.getData();
  },
  methods:{
    getData(){
        axios.get('https://covid19.mathdro.id/api')
        .then(res =>{
          let data = res.data
          this.confirmed =data.confirmed.value
          this.recovered =data.recovered.value
          this.deaths =data.deaths.value
        })
        .catch(err=>{
          console.error(err);
        })
    }
  }

}
</script>

<style scoped>

.topbar {
  margin: 2% 0% 0%;
}

</style>