<template>
  <div class="main">
    <form @submit.prevent="submitProduct">
      <h2>Products <span>Form</span></h2>
      <div class="form-group">
        <label for="name">Product Name:</label> <br />
        <input type="text" v-model="product.name" required />
      </div>
      <div class="form-group">
        <label for="price">Price:</label> <br />
        <input type="number" v-model="product.price" required />
      </div>
      <div class="form-group">
        <label for="description">Description:</label> <br />
        <textarea v-model="product.description" required></textarea>
      </div>
      <button type="submit">Add Product</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      product: {
        name: '',
        price: null,
        description: '',
      },
    };
  },
  methods: {
    submitProduct() {
      // Emit the product data to the parent component
      this.$emit('add-product', { ...this.product });

      // Clear the form fields
      this.product.name = '';
      this.product.price = null;
      this.product.description = '';

      // Redirect to the products page
      this.$router.push({ name: 'product-list' }); // Adjust the route name according to your router setup
    },
  },
};
</script>

<style scoped>
.main {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 70vh;
}

form {
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 1100px;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
}

.form-group {
  width: 1000px;
  outline: none;
  margin-bottom: 20px;
}

input {
  width: 100%;
  height: 40px;
  backdrop-filter: blur(20px);
  background: transparent;
  padding: 0 30px 0 5px;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 10px;
}

h2 {
  text-align: center;
  font-size: 30px;
  font-weight: 400;
}

h2 span {
  color: rgb(9, 7, 6);

}

textarea {
  width: 100%;
  height: 100px;
  outline: none;
  border: 1px solid rgba(0, 0, 0, 0.1);
  background: transparent;
  backdrop-filter: blur(20px);
  padding: 0 30px 0 5px;
  resize: none;
}

button {
  padding: 10px 40px;
  margin-top: 20px;
  border-radius: 8px;
  border: 2px solid #fff;
  outline: none;
  background: transparent;
  backdrop-filter: blur(100px);
  color: #020101;
  font-size: 18px;
  cursor: pointer;
  transition: 0.2s ease-in-out;
}

button:hover {
  background: rgba(103, 101, 101, 0.2);
}
</style>
