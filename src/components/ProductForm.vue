<template>
    <div>
        <h2>Add New Product</h2>
        <form @submit.prevent="submitForm">
            <div>
                <label for="name">Product Name:</label>
                <input type="text" v-model="productName" required />
            </div>

            <div>
                <label for="price">Price:</label>
                <input type="number" v-model="productPrice" required />
            </div>

            <div>
                <label for="description">Description:</label>
                <textarea v-model="productDescription" required></textarea>
            </div>

            <button type="submit">Add Product</button>
        </form>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            productName: '',
            productPrice: '',
            productDescription: ''
        };
    },
    methods: {
        submitForm() {
            // Emitting event with the new product details
            this.$emit('add-product', {
                name: this.productName,
                price: this.productPrice,
                description: this.productDescription
            });
            // Reset form fields after submission
            this.productName = '';
            this.productPrice = '';
            this.productDescription = '';
        }
    }
};
</script>
  
<style scoped>
/* Add styles here */
</style>
  