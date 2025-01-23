<!-- ./pages/products/index.vue -->
<script setup lang="ts">
const products = ref([
  {
    id: 1,
    title: "iPhone 9",
    description: "An apple mobile which is nothing like apple",
    price: 549,
    discountPercentage: 12.96,
    thumbnail: "https://i.dummyjson.com/data/products/1/thumbnail.jpg",
  },
  {
    id: 2,
    title: "iPhone X",
    description:
      "SIM-Free, Model A19211 6.5-inch Super Retina HD display with OLED technology A12 Bionic chip with ...",
    price: 899,
    discountPercentage: 17.94,
    thumbnail: "https://i.dummyjson.com/data/products/2/thumbnail.jpg",
  },
  {
    id: 3,
    title: "Samsung Universe 9",
    description:
      "Samsung's new variant which goes beyond Galaxy to the Universe",
    price: 1249,
    discountPercentage: 15.46,
    thumbnail: "https://i.dummyjson.com/data/products/3/thumbnail.jpg",
  },
]);

const formatPrice = (value: number) => {
  return new Intl.NumberFormat("en-US", {
    style: "currency",
    currency: "USD",
  }).format(value);
};
</script>
<template>
  <header class="site-section">
    <h1>Products</h1>
    <p>
      Browse our products and find the best deals. It's not a promise. It's a
      guarantee!
    </p>
  </header>
  <section class="site-section">
    <ul class="product-list">
      <li
        v-for="product in products"
        :key="product.id"
        class="product-list__item"
      >
        <article class="product-card">
          <div class="product-card__image">
            <img :src="product.thumbnail" :alt="product.title" />
          </div>
          <div class="product-card__content">
            <h2 class="product-card__title">{{ product.title }}</h2>
            <p class="product-card__description">{{ product.description }}</p>
            <div class="product-card__price">
              <span class="product-card__price--discounted">{{
                formatPrice(
                  product.price -
                    product.price * (product.discountPercentage / 100)
                )
              }}</span>
            </div>
            <div class="product-card__actions">
              <button class="product-card__actions--add-to-cart">
                Add to cart
              </button>
              <button class="product-card__actions--view-details">
                View details
              </button>
            </div>
          </div>
        </article>
      </li>
    </ul>
  </section>
</template>