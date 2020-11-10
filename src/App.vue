<template>
  <v-app>
    <v-main>
      <CompanyData/>
    </v-main>
  </v-app>
</template>

<script>
import CompanyData from './components/CompanyData';

export default {
  name: 'App',

  components: {
    CompanyData
  },

  data: () => ({
    //
  }),
};
</script>
