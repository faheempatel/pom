<style>
  @import url(https://fonts.googleapis.com/css?family=Lato:300);

  * {
    margin: 0;
    padding: 0;
  }

  html,
  body { height: 100%; }

  body {
    align-items: center;
    background:
      radial-gradient(
        ellipse at center,
        rgba(255, 255, 255, 1) 0%,
        rgba(229, 229, 229, .85) 100%
      );
    background-position: center;
    display: flex;
    font-family: Lato, Helvetica, sans-serif;
    justify-content: center;
    text-align: center;
  }
</style>

<template>
  <div>
    <calc 
      label="Price" 
      v-model="price"
      v-bind:currency="currency"
    ></calc>
    <calc 
      label="Shipping" 
      v-model="shipping"
      v-bind:currency="currency"
    ></calc>
    <calc 
      label="Handling" 
      v-model="handling"
      v-bind:currency="currency"
    ></calc>
    <calc 
      label="Discount" 
      v-model="discount"
      v-bind:currency="currency"
    ></calc>
    <p>Total: {{ currency }}{{ total }}</p>
  </div>
</template>

<script>
  import Calc from './components/calc'
  export default {
    components: {
      Calc
    },
    data: function () {
      return {
        currency: '£',
        price: 10,
        shipping: 0,
        handling: 0,
        discount: 0
      }
    },
    computed: {
      total: function () {
        return ((
          this.price * 100 +
          this.shipping * 100 +
          this.handling * 100 -
          this.discount * 100
        ) / 100).toFixed(2)
      }
    }
  }
</script>
