<template>
  <div
    v-if="products.length > 0"
    class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4"
  >
    <ProductCard
      v-for="product in products"
      :key="product.id"
      :product="product"
      @click="$emit('product-click', product)"
    />
  </div>
  <div v-else class="text-center py-10">
    <p class="text-gray-500 text-lg">
      No products found. Try a different search term.
    </p>
  </div>
</template>

<script setup>
import ProductCard from "./ProductCard.vue";

defineProps({
  products: {
    type: Array,
    required: true,
  },
});

defineEmits(["product-click"]);
</script>
