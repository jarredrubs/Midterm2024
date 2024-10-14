<template>
  <div>
    <ProductForm @add-product="addProduct" />
    <ProductList :products="products" @edit-product="editProduct" />
  </div>
</template>

<script>
import ProductForm from '../components/ProductForm.vue';
import ProductList from '../components/ProductList.vue';

export default {
  components: {
    ProductForm,
    ProductList
  },
  data() {
    return {
      products: []
    };
  },
  methods: {
    addProduct(product) {
      this.products.push(product);
    },
    editProduct({ index, updatedProduct }) {
      this.products.splice(index, 1, updatedProduct);
    }
  }
};
</script>

<style scoped>
/* Add styles here */
</style>
