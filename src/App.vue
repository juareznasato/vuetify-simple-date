<template>
  <v-app id="inspire">
    <v-card-title>
      <v-toolbar dark class="elevation-2" color="cyan">
        <v-toolbar-title>vuetify-simple-date</v-toolbar-title>
      </v-toolbar>
    </v-card-title>
    <v-card-text>
      <v-container>
        <v-row>
          <v-col cols="4" sm="4" md="4">
            <VuetifySimpleDate
              v-model="value"
              v-bind:label="label"
              v-bind:clearable="clearable"
              v-bind:readonly="readonly"
              v-bind:outlined="outlined"
              v-bind:backgroundColor="backgroundColor"
              v-bind:options="options"
            />
            Parent v-model: {{ value }} milliseconds
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="4" sm="4" md="4">
            <VuetifySimpleDate
              v-model="value2"
              v-bind:label="label2"
              v-bind:clearable="clearable2"
              v-bind:readonly="readonly2"
              v-bind:outlined="outlined2"
              v-bind:backgroundColor="backgroundColor2"
              v-bind:options="options2"
            />
            Parent v-model: {{ value2 }} milliseconds
          </v-col>
        </v-row>
      </v-container>
    </v-card-text>
  </v-app>
</template>

<script>
import VuetifySimpleDate from "./components/VuetifySimpleDate.vue";

export default {
  name: "app",
  components: {
    VuetifySimpleDate,
  },
  data: () => ({
    value: 1569639600000, // 1577239200000=>12/05/2019 00:00:00  1557673468418=>12/05/2019 12:04:28
    label: "Data dd/mm/aaaa",
    clearable: true,
    readonly: false,
    outlined: true,
    backgroundColor: "grey",
    options: {
      format: "DD/MM/YYYY", // DD/MM/YYYY HH:mm:ss
      icon: "mdi-calendar",
      errorMessage: "Data Inválida",
    },

    value2: 1569717750000, // 1577239200000=>12/05/2019 00:00:00  1557673468418=>12/05/2019 12:04:28
    label2: "Date yyyy-mm-dd hh:mm:ss",
    clearable2: true,
    readonly2: false,
    outlined2: true,
    backgroundColor2: "grey",
    options2: {
      format: "YYYY-MM-DD HH:mm:ss", // DD/MM/YYYY HH:mm:ss
      icon: "mdi-calendar",
      errorMessage: "Invalid date",
    },
  }),
};
</script>
