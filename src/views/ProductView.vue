<template>
  <section>
    <h2>Товары</h2>
    <div class="products">
      <div class="product" v-for="product in products">
        <div>{{ product.title }}</div>
        <div><img :src="product.thumbnail" alt="{{ product.title }}"></div>
        <div class="price">
          <div>{{ product.price }} $</div>
          <div><button class="btn btn-purchase">Купить</button></div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
  .products {
    display: flex;
    flex-wrap: wrap;
  }
  .product {
    width: 300px;
    margin: 40px 20px;
    background: aquamarine;
  }
  .product img {
    width: 280px;
    margin: 10px;
  }
  .product .price {
    display: flex;
    justify-content: space-between;
    margin: 20px 10px;
  }
  .product .price div:first-child {
    padding: 10px 20px;
  }
  .btn {
    outline: none;
    border: none;
    padding: 10px 20px;
  }
  .btn-purchase {
    background: #e7db96;
  }
  .btn-purchase:hover {
    cursor: pointer;
  }
</style>

<script>
export default {
  data() {
    return {
      products: []
    }
  },
  created() {
    this.getProducts();
  },
  methods: {
    getProducts() {
      fetch('https://dummyjson.com/products')
          .then(response => response.json())
          .then(data => this.products = data.products)
    }
  }
}
</script>