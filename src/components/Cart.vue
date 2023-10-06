<template>
<div class="card" v-for="product in cart" :key="product.id">
        <h3> {{ product.name }}</h3>
        <img :src="product.thumbnail" alt="">
        <h5 class="price"> Price: ${{ product.price }}</h5>
        <p class="description">Description: {{ product.description }}</p>
        <button v-on:click="removeFromCart(product)">Remove from cart</button>
    </div>    
    <div>
        <p v-if="totalPrice">Total Price: ${{ totalPrice }}</p>
        <button v-if="totalPrice" @click="checkOut()">Check Out</button>
    </div>
</template>

<script>
import 'sweetalert2/dist/sweetalert2.min.css';

export default {
    props: ['cart'],
    computed: {
        totalPrice() {
            return this.cart.reduce((total, product) => total + product.price, 0);
    }
},
    methods: {
        removeFromCart(product) {
        this.$emit("removeFromCart", product);
      }       
    },
    checkOut() {
        Swal.fire('Any fool can use a computer')
    },
  }


</script>