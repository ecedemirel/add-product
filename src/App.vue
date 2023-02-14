<template>
  <div class="container">
    <h1 class="text-center">Add Product</h1>
    <br><br>
    <app-new-product></app-new-product>
    <br><br>
    <app-progress></app-progress>
    <br><br>

    <app-products></app-products>
  </div>
</template>

<script>
import NewProduct from './components/NewProduct.vue';
import Progress from './components/Progress.vue';
import Products from './components/Products.vue';

export default {
  components: {
    appNewProduct: NewProduct,
    appProgress: Progress,
    appProducts: Products
  }
}
</script>

<style>
body {
  color: aliceblue;
  background-image: url('./assets/e-commerce-gfc7f02641_1920.png');
  background-size: cover;
  padding-top: 20px;
  padding-bottom: 20px;
}

.card {
  color: black;
  margin-right: 15px;
  margin-bottom: 15px;
  padding-top: 2%;
}


.col-md-2 {
  max-width: 20.666667% !important;
}

.product-container {
  margin: auto;
  display: flex;
  justify-content: center;
}
</style>