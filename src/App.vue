<template>
  <div class="min-h-screen bg-gray-50">
    <AppHeader
      v-model:searchQuery="searchQuery"
      @reset-category="selectedCategory = null"
    />

    <main class="container mx-auto px-4 py-6">
      <CategoryTabs
        :categories="categories"
        :selectedCategory="selectedCategory"
        @update:selectedCategory="selectedCategory = $event"
      />

      <ProductGrid
        :products="filteredProducts"
        @product-click="openContactModal"
      />
    </main>

    <ContactModal
      :show="showContactModal"
      :product="selectedProduct"
      @close="showContactModal = false"
    />

    <AppFooter @reset-category="selectedCategory = null" />
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import AppHeader from "./components/AppHeader.vue";
import CategoryTabs from "./components/CategoryTabs.vue";
import ProductGrid from "./components/ProductGrid.vue";
import ContactModal from "./components/ContactModal.vue";
import AppFooter from "./components/AppFooter.vue";
import { products } from "./data/products.js";

// Extract unique categories
const categories = computed(() => {
  return [...new Set(products.map((product) => product.category))];
});

const searchQuery = ref("");
const selectedCategory = ref(null);
const showContactModal = ref(false);
const selectedProduct = ref(null);

// Filter products based on search query and selected category
const filteredProducts = computed(() => {
  return products.filter((product) => {
    const matchesSearch =
      product.name.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
      product.id.toLowerCase().includes(searchQuery.value.toLowerCase());
    const matchesCategory =
      selectedCategory.value === null ||
      product.category === selectedCategory.value;
    return matchesSearch && matchesCategory;
  });
});

// Open contact modal with selected product
const openContactModal = (product) => {
  selectedProduct.value = product;
  showContactModal.value = true;
};
</script>
