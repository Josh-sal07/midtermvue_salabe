<template>
  <div class="container">
    <ul>
      <li v-for="(product, index) in products" :key="index">
        <span>{{ product.name }} - ${{ product.price }}</span>
        <button @click="editProduct(index)">Edit</button>

        <div class="man" v-if="editingIndex === index">
          <input v-model="product.name" />
          <input v-model="product.price" type="number" />
          <textarea v-model="product.description"></textarea>
          <button @click="saveProduct(index)">Save</button>
          <button @click="cancelEdit">Cancel</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['products'],
  data() {
    return {
      editingIndex: null,
    };
  },
  methods: {
    editProduct(index) {
      this.editingIndex = index;
    },
    saveProduct(index) {
      this.$emit('edit-product', { index, product: this.products[index] });
      this.editingIndex = null;
    },
    cancelEdit() {
      this.editingIndex = null;
    }
  },
};
</script>

<style scoped>

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 10px 0;
  margin-left: 600px;
}
.man{
  border-radius: 10px;
}

input, textarea {
  display: block;
  margin: 5px 0;
}
</style>
