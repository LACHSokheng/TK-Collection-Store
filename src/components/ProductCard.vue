<template>
  <div
    class="bg-white rounded-lg shadow-md overflow-hidden hover:shadow-lg transition-all duration-300 cursor-pointer transform hover:-translate-y-1"
    @click="$emit('click', product)"
  >
    <div class="relative pb-[100%] bg-gray-100">
      <img
        :src="product.image"
        :alt="product.name"
        class="absolute inset-0 w-full h-full object-cover"
      />
      <div class="absolute top-2 right-2">
        <span
          class="px-2 py-1 bg-white bg-opacity-90 text-xs rounded-full text-gray-600 font-medium"
        >
          {{ product.category }}
        </span>
      </div>
    </div>
    <div class="p-4">
      <div class="flex justify-between items-start mb-2">
        <h3 class="font-semibold text-gray-800 text-sm leading-tight">
          {{ product.name }}
        </h3>
      </div>
      <div class="text-xs text-gray-500 mb-3">ID: {{ product.id }}</div>
      <div class="flex justify-between items-end">
        <div>
          <div class="text-blue-600 font-bold text-lg">
            ${{ product.priceUSD }}
          </div>
          <div class="text-gray-500 text-xs">
            {{ formatKHR(product.priceKHR) }}
          </div>
        </div>
        <button
          class="bg-blue-600 text-white px-3 py-1 rounded-full text-xs hover:bg-blue-700 transition-colors"
        >
          Contact
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  product: {
    type: Object,
    required: true,
  },
});

defineEmits(["click"]);

// Format KHR price with currency symbol
const formatKHR = (price) => {
  return new Intl.NumberFormat("en-US").format(price) + " ៛";
};
</script>
