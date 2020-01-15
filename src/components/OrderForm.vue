<template>
  <div class="grid-inside">
    <p>
      OrderForm
    </p>
    <table class="product-table">
      <tr>
        <th>Item</th>
        <th>Price</th>
        <th>Include</th>
      </tr>    
      <tr v-for="(product, productIndex) in products" v-bind:key="productIndex">
        <td>{{ product.item }}</td>
        <td>{{ product.price }}</td>
        <td><input type="checkbox" v-bind:id="productIndex" v-bind:value="productIndex" v-model="checkedProducts"></td>
      </tr>
    </table>
    Total Price: {{ totalPrice }}
  </div>
</template>

<script>

export default {
  name: 'OrderForm',
  data: function() {
    return {
      checkedProducts: [],
    }
  },
  props: {
    products: {
      type: Array
    }
  },
  computed: {
    totalPrice: function() {
      let sum = 0
      for (const checkedProduct of this.checkedProducts) {
        sum += this.products[checkedProduct].price
      }
      return sum
    }
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.product-table {
  margin-left: 5%;
  width: 90%;
}

.product-table tr th {
  width: 30%;
}

.product-table tr td {
  padding-top: 0.2em;
  padding-bottom: 0.2em;
}

tr:nth-child(even) {
  background-color: rgba(255, 255, 255, 0.25);
}

</style>
