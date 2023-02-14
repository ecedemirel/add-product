<template>
  <div class="row justify-content-center align-items-stretch">
    <div class="col-md-4">
      <div class="col-md-15 card">
        <div class="card-body tex-center d-flex align-items-center flex-column">
          <img height="157" class="img-responsive text-center mb-3" :src="product.selectedImage == null ? '/src/assets/default.png' : product.selectedImage">
          <input ref="file" type="file" style="display: none;" @change="onChange($event)" class="form-control">
          <button class="btn btn-outline-secondary " type="button" @click="$refs.file.click()">Choose an image</button>
        </div>
      </div>
    </div>
    <div class="col-md-5">
      <div class="col-md-15 card">
        <div class="card-body">
          <div class="form-group">
            <label>Product Name</label>
            <input type="text" v-model="product.title" class="form-control" placeholder="Enter the name" required>
          </div>
          <div class="row">
            <div class="form-group col-md-6">
              <label>Quantity</label>
              <input type="number" v-model="product.count" class="form-control" placeholder="Enter the quantity" required>
            </div>
            <div class="form-group col-md-6">
              <label>Price</label>
              <input type="number" step="0.1" v-model="product.price" class="form-control" placeholder="Enter the price" required>
            </div>
          </div>
          <button class="btn btn-outline-info btn-block" @click="addProduct">Add</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      product: {
        id: null,
        title: '',
        count: null,
        price: null,
        totalPrice: null,
        selectedImage: null
      }
    }
  },
  methods: {
    onChange(e) {
      const file = e.target.files[0];
      this.product.selectedImage = URL.createObjectURL(file);
    },
    addProduct() {
      this.product.totalPrice = this.product.count * this.product.price
      this.emitter.emit('productAdded', this.product)
      this.product = {
        id: Math.random(),
        title: '',
        count: null,
        price: null,
        totalPrice: null,
        selectedImage: null
      }
    }
  }
}
</script>