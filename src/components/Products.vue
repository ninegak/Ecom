<template>
    <div class="container">
      <div class="card" v-for="(product, index) in items" :key="product.id">
        <h3> {{ product.name }}</h3>
        <img :src="product.thumbnail" alt="">
        <h5 class="price"> Price: ${{ product.price }}</h5>
        <p class="description">Description: {{ product.description }}</p>
        <button v-on:click="AddItemTocrat(product)">Add to cart</button>
    </div>
    </div>
</template>

<script>
import items from '../views/data/items.js'

export default {
    name: 'Products',
    data () {
      return {
        items: items,
      }
    },
    methods : {
      AddItemTocrat(product) {
        this.$emit("AddItemTocrat", product);
      },
    },
  }
</script>

<style>

.container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;  
}
.container .card {
  margin-top: 65px;
  
 }
 img {
  height: 150px;
 }
</style>