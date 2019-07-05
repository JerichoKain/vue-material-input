<template>
  <div id="app">
    <md-app>
      <md-app-content>
        <md-field>
          <label>Number</label>
          <md-input ref="field" v-model="num" type="Number" v-on:input="updateValidity" />
        </md-field>
        Number is: '{{ num }}' <br />
        ValidityState:
        <ul>
          <li>BadInput:{{ validity.badInput }}</li>
          <li>Custom Error:{{ validity.customError }}</li>
          <li>Pattern Mismatch:{{ validity.patternMismatch }}</li>
          <li>Range Overflow:{{ validity.rangeOverflow }}</li>
          <li>Range Underflow:{{ validity.rangeUnderflow }}</li>
          <li>Step Mismatch:{{ validity.stepMismatch }}</li>
          <li>Too Long:{{ validity.tooLong }}</li>
          <li>Too Short:{{ validity.tooShort }}</li>
          <li>Type Mismatch:{{ validity.typeMismatch }}</li>
          <li>Valid:{{ validity.valid }}</li>
          <li>Value Missing:{{ validity.valueMissing }}</li>
        </ul>
        <md-divider />
        Steps to reproduce:
        <ol>
          <li>Enter an invalid number (e.g. 11.11.11)</li>
          <li>Notice that 'num' value has cleared</li>
          <li>Click off the field</li>
          <li>Notice that the label goes over the value that is in the input</li>
        </ol>
      </md-app-content>
    </md-app>
  </div>
</template>

<script>
export default {
  name: "app",
  components: {},
  data() {
    return {
      num: 11.11,
      validity: {}
    }
  },
  methods:{
    updateValidity() {
      this.validity = this.$refs.field.$el.validity;
    }
  }
}
</script>

<style>
</style>
