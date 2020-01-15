<template>
  <div class="grid-inside">
    <h2>
      ProductListOrGrid
    </h2>
    <input type="checkbox" id="checkbox" v-model="displayGrid">

    <table v-if="!displayGrid" class="product-table">
      <tr>
        <th>Item</th>
        <th>Image</th>
      </tr>    
      <tr class="product-row" v-for="(product, productIndex) in products" :key="productIndex">
        <td><div>{{ product.item }}</div></td>
        <td><img class="product-image" :src="product.image"></td>
      </tr>
    </table>

    <div v-if="displayGrid" id="productListGrid" class="centre">
      <div class="product-row" v-for="(product, productIndex) in products" :key="productIndex">
      <img :src="product.image">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductListOrGrid',
  data: function() {
    return {
      displayGrid: false
    }
  },
  props: {
    products: {
      type: Array
    }
  },
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
  margin-left: 30%;
}

.product-row {
  height: 6em;
}
.product-row div {
  margin-top: 2em;
}
img {
  margin-top: 0.5em;
  margin-bottom: 0.5em;
  height: 5em;
}


#productListGrid {
  display: grid;
  grid-template-rows: repeat(3, 20%);
  grid-row-gap: 2em;
	grid-template-columns: repeat(3, 20%);
  grid-column-gap: 1.5em;

	padding: 0px;
  margin-top: 0px;

  margin-left: 24%;
}

</style>
