# vuetify-simple-date

If you use Vuejs with Vuetify and need a component to input mask dates working in milliseconds. Maybe it can help you.


input:
- 14/05/2019

v-model: (milliseconds)
1557802800000

if you want a milliseconds datetime picker component, you can try this:
<p><a href="https://github.com/juareznasato/vuetify-datetime.git" target="_blank">vuetify-datetime</a></p>

## Dependency
- VueJS
- Vuetify&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$ npm install vuetify --save
- moment&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$ npm install moment --save 
- vue-the-mask&nbsp;&nbsp;$ npm install vue-the-mask --save
- @mdi/font&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$ npm install @mdi/font -D --save

## Links
<p><a href="https://k6kzp.csb.app/">See DEMO here</a></p>
<p><a href="https://github.com/juareznasato/vuetify-simple-date" target="_blank">GitHub</a></p>
<p><a href="https://www.npmjs.com/package/vuetify-simple-date" target="_blank">npm</a></p>

## Install:
```
$ npm install vuetify-simple-date --save

Register component:

1- Create a src/plugins/vuetify-simple-date.js file with:
import Vue from "vue";
import VuetifySimpleDate from "vuetify-simple-date";
Vue.use(VuetifySimpleDate);
export default VuetifySimpleDate;

2- Add to src/mains.js file:
import "./plugins/vuetify-simple-date.js";

Parent component:
<template>
  <div>
     <vuetify-simple-date v-model="value" v-bind:label="label" v-bind:options="options" />
     Parent v-model: {{ value }} milliseconds
  </div>
</template>
<script>
export default {
  data: () => ({
    value: 1569717750000,
    label: "Date yyyy-mm-dd hh:mm:ss",
    options: {
      format: "YYYY-MM-DD",     // or others formats. YYYY-MM-DD HH:mm:ss for example
      clearable: true,
      readonly: false,
      icon: "mdi-calendar",
      errorMessage: "Invalid date"
    }
  })
};
</script>

