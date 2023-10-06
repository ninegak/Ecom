<template>
  <header>
    <router-link to="/">Ragnarok</router-link>
    <nav class="navbar">
    <button class="astext" @click="navigateTo('products')">View Products</button>
    <button class="astext" @click="navigateTo('cart')">Cart {{cart.length}}</button>
  </nav>
  </header>
  <div v-if="page === 'cart'">
    <Cart v-on:removeFromCart="removeFromCart" :cart="cart"/>
  </div>

  <div v-if="page === 'products'">
  <Products v-on:AddItemTocrat="AddItemTocrat" />
  </div>
</template>

<script>
import items from './data/items.js'
import Products from '../components/Products.vue'
import Cart from '../components/Cart.vue'

export default {
    name: 'Home',
    data () {
      return {
        page: 'products',
        cart: [],
        items: items,
        product: null
      }
    },
    components: {
      Products, Cart
    },
    methods : {
      AddItemTocrat(product) {
        this.cart.push(product)
        console.log(this.cart);
      },
      navigateTo(page) {
        this.page = page
      },
      removeFromCart(product) {
        this.cart.splice(this.cart.indexOf(product), 1);
      },
      totalPrice() {
        return this.product.price
      },
    },
  }
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}


header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    padding: 20px 100px;
    justify-content: space-between;
    display: flex;
    align-items: center;
    z-index: 100;
    background-color: #6B8A47;
}

a {
    color: #eae3c0;
    text-decoration: none;
}

.card {
        width: 80%;
        margin: 10%;
        padding: 10px;
        border-radius: 5px;
        box-shadow: 0 0 5px;
    }
    .card h5 {
        color: gray;
    }

    button {
    cursor: pointer;
  }

@media (min-width: 500px) {
  .card {
    width: 350px;
    margin: 10px;
  }
  
}

.astext {
    background:none;
    border:none;
    cursor: pointer;
    color: #eae3c0;
}

.navbar a{
    position: relative;
    font-size: 18px;
    font-weight: 500;
    margin-left: 40px;
    margin-right: 35px;
}

.navbar a:hover,
.navbar a.active {
    color: orange;
}

.navbar a::before {
    content: '';
    position: absolute;
    top: 100%;
    left: 0;
    width: 0;
    height: 2px;
    background-color: #fff;
    transition: 0.3s;
}

.navbar a:hover::before {
    width: 100% ;
}
</style>

