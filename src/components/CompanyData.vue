<template>
  <v-container>
    <v-layout column wrap align-center>
    <v-flex class="text-xs-center">
    <v-col class="mb-4">
      <h1 class="display-2 font-weight-bold mb-3">
        Company Data
      </h1>
    </v-col>
      <v-col cols="10">
        <ol>
          <li>Name of the company: {{companyData.companyName}}</li>
          <li>Price of each share: {{companyData.latestPrice}}</li>
          <li>Total company value: {{companyData.marketCap}}</li>
        </ol>
      </v-col>
      <v-row class="mb-5" cols="10">
        <v-btn @click="getCompanyData">Get data</v-btn>
        <v-btn @click="buyShares">Buy</v-btn>
      </v-row>
      <v-col class="mb-5" cols="10">
        <p>Amount: {{amount}}</p>
        <p>Shares: {{shares}}</p>
      </v-col>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      companyData:{},
      amount: 0,
      shares: 0,
    }
  },
  methods: {
    getCompanyData() {
      axios.get('https://cloud.iexapis.com/stable/stock/aapl/quote?token=sk_2e52b0cbb63547e4b5705df88b19dcf0')
        .then((response) => {
          this.companyData = response.data
        })
        console.log(this.companyData.latestPrice)
    },
    buyShares() {
      console.log("You Bougth")
      this.shares++
      this.amount = this.amount + this.companyData.latestPrice
    }
  }
}
</script>

<style lang="css">
  v-container {
    align-items: center;
  }
  ol {
    list-style: none;
  }
</style>