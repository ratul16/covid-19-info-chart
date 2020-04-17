<template>
<v-card class="topbar">
  <v-row align="center" justify="center">
    
    <v-col md="4">
        <h2 class="text-center">Total Confirmed</h2>
        <h1 class="text-center blue--text text--darken-1">{{totalResult.confirmed.value}}</h1>

    </v-col>

    <v-col md="4">
        <h2 class="text-center">Total Recovered</h2>
        <h1 class="text-center green--text text--darken-1">{{totalResult.recovered.value}}</h1>
    </v-col>

    <v-col md="4">
        <h2 class="text-center">Total Death</h2>
        <h1 class="text-center red--text text--darken-3">{{totalResult.deaths.value}}</h1>
    </v-col>
  </v-row>
</v-card>
</template>

<script>
import total from '@/assets/total.json'

export default {

  data(){
    return {
      totalResult:total
    }
  }

}
</script>

<style scoped>

.topbar {
  margin: 5% 0% 0%;
}

</style>