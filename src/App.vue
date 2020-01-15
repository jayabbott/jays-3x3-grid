<template>
  <div id="app">
    <div id="grid-1" class="grid-item">
      <DigitalClock />
    </div>
    <div id="grid-2" class="grid-item">
      <LoginForm />
    </div>
    <div id="grid-3" class="grid-item">
      <Quiz />
    </div>
    <div id="grid-4" class="grid-item">
      <PersonTable :personToAdd="userPass" />
    </div>
    <div id="grid-5" class="grid-item">
      <NewPerson @inputData="userAdded" />
    </div>
    <div id="grid-6" class="grid-item">
      <OrderForm :products="products" />
    </div>
    <div id="grid-7" class="grid-item">
      <ProductSearch :products="products" />
    </div>
    <div id="grid-8" class="grid-item">
      <ProductListOrGrid :products="products" />
    </div>
    <div id="grid-9" class="grid-item">
      <MagicEightBall />
    </div>    
  </div>
</template>

<script>
import DigitalClock  from './components/DigitalClock.vue'
import LoginForm from './components/LoginForm.vue'
import Quiz from './components/Quiz.vue'
import PersonTable from './components/PersonTable.vue'
import NewPerson from './components/NewPerson.vue'
import OrderForm from './components/OrderForm.vue'
import ProductSearch from './components/ProductSearch.vue'
import ProductListOrGrid from './components/ProductListOrGrid.vue'
import MagicEightBall from './components/MagicEightBall.vue'
//
let products = [
  {item: 'Xbox', price: 200, image: require('./assets/product-images/xbox.jpg')},
  {item: 'Alarm Clock', price: 12.99, image: require('./assets/product-images/alarm-clock.jpg')},
  {item: 'Washing Machine', price: 119.99, image: require('./assets/product-images/washing-machine.jpg')},
  {item: '4K Monitor', price: 350, image: require('./assets/product-images/4k-monitor.jpg')},
  {item: 'Graphics Card', price: 100, image: require('./assets/product-images/graphics-card.jpg')},
  {item: 'American Fridge', price: 300, image: require('./assets/product-images/american-fridge.jpg')},
  {item: 'Playing Cards', price: 1.5, image: require('./assets/product-images/playing-cards.jpg')},
  {item: 'Sofa', price: 449.99, image: require('./assets/product-images/sofa.jpg')},
  {item: 'Desk Lamp', price: 49.98, image: require('./assets/product-images/desk-lamp.jpg')},
]

export default {
  name: 'app',
  components: {
    DigitalClock,
    LoginForm,
    Quiz,
    PersonTable,
    NewPerson,
    OrderForm,
    ProductSearch,
    ProductListOrGrid,
    MagicEightBall
  },
  data: function() {
    return {
      userPass: {},
      products: products,
    };
  },
  methods: {
    userAdded(variable) {
      this.userPass = variable;
    }
  }
}
</script>

<style>

@font-face {
  font-family: 'DSEG14Modern';
  src: url('./assets/DSEG14Modern-Bold.woff2') format('woff2'),
       url('./assets/DSEG14Modern-Bold.woff') format('woff'), 
       url('./assets/DSEG14Modern-Bold.ttf')  format('truetype');
}

@import "https://cdn.jsdelivr.net/npm/bulma@0.8.0/css/bulma.min.css";


#app {
  display: grid;
  grid-template-rows: repeat(3, 31vh);
  grid-row-gap: 1em;
	grid-template-columns: repeat(3, 32vw);
  grid-column-gap: 1em;

	padding: 0px;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}

.grid-item {
  background-image: linear-gradient(141deg, #b8d1c6 0%, #84eefa 50%, #78daff 80%);
  overflow: auto ;
}

/*DSEG14Modern-Bold.woff2*/

</style>
