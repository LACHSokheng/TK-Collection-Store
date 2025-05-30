<template>
  <header class="sticky top-0 z-10 bg-white shadow-md">
    <div class="container mx-auto px-4 py-4">
      <!-- Desktop Layout -->
      <div class="hidden md:flex justify-between items-center">
        <div
          class="flex items-center space-x-3 cursor-pointer"
          @click="resetToAllProducts"
        >
          <div class="h-10 w-10 overflow-hidden rounded-lg">
            <img
              src="/logo.jpg"
              alt="TKCollectionStore Logo"
              class="w-full h-full object-cover"
            />
          </div>
          <h1 class="text-xl md:text-2xl font-bold text-gray-800">
            TKCollectionStore
          </h1>
        </div>
        <div class="relative w-full max-w-md mx-4">
          <input
            type="text"
            :value="searchQuery"
            @input="$emit('update:searchQuery', $event.target.value)"
            placeholder="Search products..."
            class="w-full px-4 py-2 rounded-full border border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500"
          />
          <button class="absolute right-3 top-2.5 text-gray-500">
            <SearchIcon class="h-5 w-5" />
          </button>
        </div>
      </div>

      <!-- Mobile Layout -->
      <div class="md:hidden">
        <!-- Logo and Store Name Row -->
        <div
          class="flex items-center mb-3 cursor-pointer"
          @click="resetToAllProducts"
        >
          <div class="h-8 w-8 overflow-hidden rounded-lg mr-2">
            <img
              src="/logo.jpg"
              alt="TKCollectionStore Logo"
              class="w-full h-full object-cover"
            />
          </div>
          <h1 class="text-lg font-bold text-gray-800">TKCollectionStore</h1>
        </div>

        <!-- Search Bar Row -->
        <div class="relative">
          <input
            type="text"
            :value="searchQuery"
            @input="$emit('update:searchQuery', $event.target.value)"
            placeholder="Search products..."
            class="w-full px-4 py-2 pr-10 rounded-full border border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500 text-sm"
          />
          <button class="absolute right-3 top-2.5 text-gray-500">
            <SearchIcon class="h-4 w-4" />
          </button>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
import { SearchIcon } from "lucide-vue-next";

defineProps({
  searchQuery: {
    type: String,
    default: "",
  },
});

const emit = defineEmits(["update:searchQuery", "reset-category"]);

// Reset to All Products category and scroll to top
const resetToAllProducts = () => {
  // Emit event to reset category filter to "All"
  emit("reset-category");

  // Also scroll to top for better UX
  window.scrollTo({ top: 0, behavior: "smooth" });
};
</script>
