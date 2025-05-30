<template>
  <footer class="bg-gray-800 text-white py-8 mt-12">
    <div class="container mx-auto px-4">
      <div class="flex flex-col md:flex-row justify-between items-center">
        <div
          class="flex items-center space-x-3 mb-4 md:mb-0 cursor-pointer"
          @click="resetToAllProducts"
        >
          <div class="h-8 w-8 overflow-hidden rounded-lg">
            <img
              src="/logo.jpg"
              alt="TKCollectionStore Logo"
              class="w-full h-full object-cover"
            />
          </div>
          <h2 class="text-lg font-bold">TKCollectionStore</h2>
        </div>
        <div class="flex space-x-4">
          <a href="tel:069399914" class="hover:text-blue-300 transition-colors">
            <PhoneIcon class="h-5 w-5" />
          </a>
          <a
            href="https://www.facebook.com/share/15n9bbHpBM/"
            target="_blank"
            rel="noopener noreferrer"
            class="hover:text-blue-300 transition-colors"
          >
            <FacebookIcon class="h-5 w-5" />
          </a>
          <a
            href="https://t.me/CHHANSOKLAY"
            target="_blank"
            rel="noopener noreferrer"
            class="hover:text-blue-300 transition-colors"
          >
            <TelegramIcon class="h-5 w-5" />
          </a>
          <a
            href="https://maps.app.goo.gl/4r3GQdMidp67iU7w6?g_st=ac"
            target="_blank"
            rel="noopener noreferrer"
            class="hover:text-blue-300 transition-colors"
          >
            <MapPinIcon class="h-5 w-5" />
          </a>
        </div>
      </div>
      <div class="mt-4 text-center text-sm text-gray-400">
        © {{ new Date().getFullYear() }} TKCollectionStore. All rights reserved.
      </div>
    </div>
  </footer>
</template>

<script setup>
import { PhoneIcon, MapPinIcon } from "lucide-vue-next";
import FacebookIcon from "./icons/FacebookIcon.vue";
import TelegramIcon from "./icons/TelegramIcon.vue";

const emit = defineEmits(["reset-category"]);

// Reset to All Products category and scroll to top
const resetToAllProducts = () => {
  // Emit event to reset category filter to "All"
  emit("reset-category");

  // Also scroll to top for better UX
  window.scrollTo({ top: 0, behavior: "smooth" });
};
</script>
