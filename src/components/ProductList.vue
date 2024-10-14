<template>
    <div>
        <h2>Product List</h2>
        <ul v-if="products.length">
            <li v-for="(product, index) in products" :key="index">
                <span v-if="!isEditingIndex(index)">
                    {{ product.name }} - ${{ product.price }} - {{ product.description }}
                    <button @click="editProduct(index)">Edit</button>
                </span>

                <span v-else>
                    <input v-model="editProductData.name" />
                    <input v-model="editProductData.price" type="number" />
                    <textarea v-model="editProductData.description"></textarea>
                    <button @click="saveEdit(index)">Save</button>
                    <button @click="cancelEdit">Cancel</button>
                </span>
            </li>
        </ul>
        <p v-else>No products available.</p>
    </div>
</template>
  
<script>
export default {
    props: ['products'],
    data() {
        return {
            editProductData: {
                name: '',
                price: '',
                description: ''
            },
            editingIndex: null
        };
    },
    methods: {
        editProduct(index) {
            this.editingIndex = index;
            this.editProductData = { ...this.products[index] };
        },
        saveEdit(index) {
            this.$emit('edit-product', { index, updatedProduct: this.editProductData });
            this.editingIndex = null;
        },
        cancelEdit() {
            this.editingIndex = null;
        },
        isEditingIndex(index) {
            return this.editingIndex === index;
        }
    }
};
</script>
  
<style scoped>
/* Add styles here */
</style>
  