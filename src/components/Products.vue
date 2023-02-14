<template>
  <div v-if="products.length > 0">
    <h3 class="text-center">List of Products</h3>
    <hr>
    <div class="row product-container">
      <app-product v-for="product in products">
        <img class="card-img-top" :src="product.selectedImage" :alt="product.title">
        <div class="card-body">
          <h5 class="card-title">{{ product.title }}</h5>
          <small>
            <strong>Quantity: </strong> {{ product.count }}
          </small>
          <br>
          <small>
            <strong>Price: </strong> {{ product.price }}
          </small>
          <br>
          <small>
            <strong>Total: </strong> {{ product.totalPrice }}
          </small>
          <div class="mt-3">
            <button class="btn btn-outline-danger btn-block" @click="deleteProduct(product.id)">Delete</button>
          </div>
        </div>
      </app-product>
    </div>
  </div>
</template>

<script>
import Product from './Product.vue';

export default {
  data() {
    return {
      products: []
    }
  },
  components: {
    appProduct: Product
  },
  methods: {
    deleteProduct(id) {
      let products = this.products.filter((el) => el.id !== id);
      this.products = products;
      this.emitter.emit('productDeleted', this.products.length)
    }
  },
  created() {
    this.emitter.on('productAdded', (product) => {
      if (this.products.length >= 10) {
        alert("You cannot add more products!")
      }
      else {
        this.products.push(product)
        this.emitter.emit('progressBarUpdated', this.products.length)
      }
    })
  }
}
</script>