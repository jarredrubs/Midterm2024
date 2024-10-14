<script setup>
import { RouterLink, RouterView } from 'vue-router';
import { ref } from 'vue';
import ProductForm from './components/ProductForm.vue';
import ProductList from './components/ProductList.vue';

// Reactive product list
const products = ref([]);

// Method to add a new product
const addProduct = (product) => {
  products.value.push(product);
};

// Method to edit an existing product
const editProduct = ({ index, updatedProduct }) => {
  products.value.splice(index, 1, updatedProduct);
};
</script>

<template>
  <div>
    <!-- Navigation Links (for routing between Home and Products page) -->
    <nav>
      <router-link to="/home">Home</router-link> <!-- Home page link -->
      <router-link to="/products">Products</router-link> <!-- Products page link -->
    </nav>

    <!-- Router View to display different components (Home, Products, etc.) -->
    <router-view />
  </div>
</template>

<style scoped>
/* Basic styling for the navigation bar */
nav {
  background-color: #4a90e2;
  /* Bright blue background */
  padding: 15px;
  border-radius: 8px;
  /* Rounded corners */
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
  /* Slight shadow */
}

nav a {
  color: white;
  text-decoration: none;
  margin: 0 15px;
  font-weight: bold;
  transition: color 0.3s;
  /* Smooth color transition */
}

nav a:hover {
  color: #ffd700;
  /* Gold color on hover */
}

/* General page layout */
body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  /* Modern font */
  margin: 0;
  padding: 0;
  background-color: #f0f4f8;
  /* Light background color */
}

/* Container for the form and product list */
.container {
  max-width: 800px;
  /* Slightly narrower container */
  margin: 30px auto;
  padding: 20px;
  background-color: #ffffff;
  /* White background */
  border-radius: 12px;
  /* More rounded corners */
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  /* Deeper shadow for emphasis */
}

/* Styling for the product form */
form {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

form input,
form textarea {
  margin-bottom: 15px;
  /* Increased margin for better spacing */
  padding: 12px;
  /* Increased padding for inputs */
  border-radius: 6px;
  /* Rounded corners for inputs */
  border: 1px solid #ccc;
  /* Light border */
  transition: border-color 0.3s;
  /* Smooth border color transition */
}

form input:focus,
form textarea:focus {
  border-color: #4a90e2;
  /* Blue border on focus */
  outline: none;
}

button {
  padding: 12px 25px;
  /* Adjusted button padding */
  background-color: #4caf50;
  /* Green background for buttons */
  color: white;
  border: none;
  border-radius: 6px;
  /* Rounded corners for buttons */
  cursor: pointer;
  transition: background-color 0.3s;
  /* Smooth background color transition */
}

button:hover {
  background-color: #45a049;
  /* Darker green on hover */
}

/* Styling for the product list */
ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  background-color: #e8f0fe;
  /* Light blue background for list items */
  padding: 15px;
  /* Increased padding for list items */
  border-radius: 8px;
  /* Rounded corners for list items */
  margin-bottom: 10px;
  /* Spacing between list items */
  transition: background-color 0.3s;
  /* Smooth background transition */
}

li:hover {
  background-color: #d4e1fc;
  /* Slightly darker blue on hover */
}

.edit-button {
  background-color: #2196f3;
  /* Bright blue for edit buttons */
  color: white;
  padding: 8px 15px;
  /* Adjusted padding for edit buttons */
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s;
  /* Smooth background transition */
}

.edit-button:hover {
  background-color: #1976d2;
  /* Darker blue on hover */
}
</style>
