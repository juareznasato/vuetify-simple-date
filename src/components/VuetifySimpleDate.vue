<template>
  <div>
    <v-text-field
      v-model="compValue"
      v-on:keyup="emit($event.target.value)"
      v-mask="compMask"
      v-bind:label="label"
      v-bind:color="color"
      v-bind:prepend-icon="options.icon"
      v-bind:readonly="options.readonly"
      v-bind:clearable="options.clearable"
      v-bind:outlined="options.outlined"
      v-bind:hint="showHint===true ? options.errorMessage : ''"
      v-on:change="$emit('change')"
      v-on:input="$emit('input')"
      v-on:keydown="$emit('keydown')"
      v-on:focus="$emit('focus')"
      v-on:blur="$emit('blur')"
    ></v-text-field>
  </div>
</template>

<script>
import moment from "moment";
import { mask } from "vue-the-mask";

export default {
  directives: {
    mask
  },
  model: { prop: "value", event: "input" },
  props: {
    value: {
      type: [Number, String],
      default: 0
    },
    label: {
      type: String,
      default: "Label"
    },
    options: {
      type: Object,
      default: function() {
        return { format: "DD/MM/YYYY", clearable: false, readonly: false , outlined: false, icon:"mdi-calendar", errorMessage: "Data Inválida"};
      }
    }
  },
  data: () => ({
    color: "",
    showHint: false
  }),
  computed: {
    compValue: {
      get: function() {
        return this.value ? (moment(new Date(this.value)).format(this.options.format)) : null;
      },
      set: function() {
        this.$emit("input", null);
        this.color = "";
        this.showHint = false;
      }
    },
    /* Criar mascara a partir da configuracao de formato */
    compMask: {
      get: function() {
        let format = this.options.format;
        format = this.replaceAll(format.toLowerCase(), "d", "#")
        format = this.replaceAll(format.toLowerCase(), "m", "#")
        format = this.replaceAll(format.toLowerCase(), "y", "#")
        format = this.replaceAll(format.toLowerCase(), "h", "#")
        format = this.replaceAll(format.toLowerCase(), "m", "#")
        format = this.replaceAll(format.toLowerCase(), "s", "#")
        return format;
      }
    }
  },
  methods: {
    emit(value) {
      if (value.length === this.options.format.length) {
        let stringDate = moment(value, this.options.format).format("YYYY-MM-DD HH:mm:ss");
        if (moment(stringDate, "YYYY-MM-DD  HH:mm:ss").isValid()) {
          this.$emit("input", this.stringToMillisecond(stringDate));
          this.color = "";
          this.showHint = false;
        } else {
          this.color = "red";
          this.showHint = true;
        }
      }
    },
    stringToMillisecond: function(date) {
      return Date.parse(date);
    },
    replaceAll(str, find, replace) {
      return str.replace(new RegExp(find, "g"), replace);
    },
  }
};
// Str to milli
// var d = Date.parse(date);
// milli to date
// this.date = new Date(d);
</script>
