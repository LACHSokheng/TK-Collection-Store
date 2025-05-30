<template>
  <header class="sticky top-0 z-10 bg-white shadow-md">
    <div class="container mx-auto px-4 py-4 flex justify-between items-center">
      <div class="flex items-center space-x-3">
        <div
          class="h-10 w-10 bg-gradient-to-br from-blue-500 to-purple-600 rounded-lg flex items-center justify-center"
        >
          <span class="text-white font-bold text-lg">TK</span>
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

defineEmits(["update:searchQuery"]);
</script>
