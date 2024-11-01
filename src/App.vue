<script setup>
import jsonData from '@/assets/data.json'
import ProductCard from './components/ProductCard.vue'
import { ref } from 'vue'

const productData = ref(jsonData.products)

const deleteProduct = (pos) => {
  productData.value.splice(pos,1)
}

</script>

<template>
  <header>
    <h1>E-Commerce Product Dashboard</h1>
  </header>

  <main>
    <div class="product-container flex-row" v-if="productData.length > 0">
      <ProductCard v-for="(item,count) in productData" :key="count" :data="item" @delete="deleteProduct(count)" />
    </div>
    <div v-else>
      <h2>There are no items to show!</h2>
    </div>
  </main>
</template>

<style>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

.product-container{
  flex-wrap: wrap;
  gap: 45px;
  margin: 45px 0px;
}

.flex-row{
    display:flex;
    flex-direction: row;
}
.flex-col{
    display:flex;
    flex-direction: column;
}
.space-between{
  justify-content: space-between;
}

.bold{
  font-weight: bold;
}

.big{
  font-size: 1.25em;
}

.bigger{
  font-size: 1.4em;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
