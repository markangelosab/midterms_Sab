<template>
  <div class="product-list">
    <h3>Product List</h3>
    <ul v-if="products.length">
      <li v-for="(product, index) in products" :key="index" class="product-item">
        <div v-if="editIndex !== index">
          <span>{{ product.name }} - {{ product.price }} - {{ product.description }}</span>
          <button @click="editProduct(index)">Edit</button>
        </div>
        <div v-else>
          <input v-model="editProductData.name" placeholder="Product Name" />
          <input v-model="editProductData.price" type="number" placeholder="Price" />
          <textarea v-model="editProductData.description" placeholder="Description"></textarea>
          <button @click="saveEdit(index)">Save</button>
          <button @click="cancelEdit">Cancel</button>
        </div>
      </li>
    </ul>
    <p v-else>No products added yet.</p>
  </div>
</template>

<script>
export default {
  props: {
    products: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      editIndex: -1,
      editProductData: { name: '', price: '', description: '' }
    };
  },
  methods: {
    editProduct(index) {
      this.editIndex = index;
      this.editProductData = { ...this.products[index] };
    },
    saveEdit(index) {
      this.$emit('edit-product', { index, updatedProduct: this.editProductData });
      this.editIndex = -1;
    },
    cancelEdit() {
      this.editIndex = -1;
    }
  }
};
</script>

<style scoped>
.product-list {
  margin: 20px auto;
  max-width: 600px;
  background-color: #f5f5f5;
  padding: 20px;
  border-radius: 5px;
}

.product-item {
  margin-bottom: 15px;
  list-style-type: none;
}

button {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 8px 12px;
  border-radius: 5px;
  cursor: pointer;
  margin-right: 5px;
}

button:hover {
  background-color: #358a66;
}

input,
textarea {
  padding: 8px;
  border-radius: 4px;
  border: 1px solid #ccc;
  margin-bottom: 10px;
  width: 100%;
}
</style>
