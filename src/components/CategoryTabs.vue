<template>
  <div class="mb-6 overflow-x-auto scrollbar-hide">
    <div class="flex space-x-2 min-w-max">
      <button
        @click="$emit('update:selectedCategory', null)"
        :class="[
          'px-4 py-2 rounded-full text-sm font-medium transition-colors',
          selectedCategory === null
            ? 'bg-blue-600 text-white'
            : 'bg-gray-200 text-gray-800 hover:bg-gray-300',
        ]"
      >
        All
      </button>
      <button
        v-for="category in categories"
        :key="category"
        @click="$emit('update:selectedCategory', category)"
        :class="[
          'px-4 py-2 rounded-full text-sm font-medium transition-colors',
          selectedCategory === category
            ? 'bg-blue-600 text-white'
            : 'bg-gray-200 text-gray-800 hover:bg-gray-300',
        ]"
      >
        {{ category }}
      </button>
    </div>
  </div>
</template>

<script setup>
defineProps({
  categories: {
    type: Array,
    required: true,
  },
  selectedCategory: {
    type: String,
    default: null,
  },
});

defineEmits(["update:selectedCategory"]);
</script>

<style scoped>
.scrollbar-hide {
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none; /* Firefox */
}
.scrollbar-hide::-webkit-scrollbar {
  display: none; /* Chrome, Safari and Opera */
}
</style>
