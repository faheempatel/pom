<style module>
  .test {
    color: blue;
  }
</style>

<template>
  <div>
    <label :class="$style.test" v-if="label">{{ label }}</label>
    {{ currency }}
    <input
      ref="input"
      v-bind:value="value"
      v-on:input="updateValue($event.target.value)"
    >
  </div>
</template>

<script>
  export default {
    name: 'calc',
    props: {
      currency: {
        type: String,
        default: '$'
      },
      value: {
        type: Number,
        default: 0
      },
      label: {
        type: String,
        default: ''
      }
    },
    methods: {
      updateValue: function (value) {
        this.$emit('input', parseInt(value))
      }
    }
  }
</script>
