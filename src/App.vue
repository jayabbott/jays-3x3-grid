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
      <PersonTable />
    </div>
    <div id="grid-5" class="grid-item">
      <NewPerson />
    </div>
    <div id="grid-6" class="grid-item">
      <OrderForm />
    </div>
    <div id="grid-7" class="grid-item">
      <ProductSearch />
    </div>
    <div id="grid-8" class="grid-item">
      <ProductListOrGrid />
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
