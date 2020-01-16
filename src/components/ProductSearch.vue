<template>
  <div class="grid-inside">
    <div class="columns is-mobile">
      <div class="column">
        <table v-if="productResults.length > 0" class="product-table">
          <tr>
            <th>Item</th>
            <th>Image</th>
          </tr>    
          <tr class="product-row" v-for="(product, productIndex) in productResults" v-bind:key="productIndex">
            <td><div>{{ product.item }}</div></td>
            <td><img class="product-image" :src="product.image"></td>
          </tr>
        </table>
      </div>
      <div class="column">
        <h2>Product Search</h2>

        <input id="searchInput" v-model="searchString" type="text">
      </div>
    </div>
    
  </div>
</template>

<script>

function searchProduct(productName, searchTerm)
{
  if(searchTerm == '')
  {
    return false
  }

  productName = productName.toUpperCase()
  searchTerm = searchTerm.toUpperCase()

  let searchTermLength = searchTerm.length

  let productStart = productName.substring(0, searchTermLength);

  return (productStart == searchTerm)


}

export default {
  name: 'ProductSearch',
  data: function() {
    return {
      searchString: '',
      productResults: [],
    }
  },
  props: {
    products: {
      type: Array
    }
  },
  watch: {
    searchString: function() {
      this.productResults = []
      for (const product of this.products) {
        if (searchProduct(product.item, this.searchString))
        {
          this.productResults.push(product)
        }
      }
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

.columns {
  width: 98%;
}
</style>
