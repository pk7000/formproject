<template>
  <div>
    <v-row no-gutters>
      <v-col md="3"><v-card class="pa-2 grey darken-3" outlined> id</v-card></v-col>
      <v-col md="3"><v-card class="pa-2 grey darken-3" outlined> sex</v-card></v-col>
      <v-col md="3"><v-card class="pa-2 grey darken-3" outlined> age</v-card></v-col>
      <v-col md="3"><v-card class="pa-2 grey darken-3" outlined> score</v-card></v-col>
    </v-row>
    <v-row v-for="(items, index) in $store.getters.items" :key="index"  no-gutters>
      <v-col md="3"><v-card class="pa-2" outlined> {{ index + 1 }}</v-card></v-col>
      <v-col md="3"><v-card class="pa-2" outlined> {{ items.sex }}</v-card></v-col>
      <v-col md="3"><v-card class="pa-2" outlined> {{ items.age }}</v-card></v-col>
      <v-col md="3"><v-card class="pa-2" outlined> {{ items.score }}</v-card></v-col>
      <td></td>
    </v-row>
    <v-btn class="mr-4" @click="page">กรอกแบบสอบถามอีกครั้ง</v-btn>
  </div>
</template>

<script>
export default {
  methods: {
    page() {
      this.$store.state.page = 1;
    },
  },
};
</script>

<style>
</style>