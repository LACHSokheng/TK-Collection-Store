<template>
  <div
    v-if="show"
    class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-20 p-4"
  >
    <div class="bg-white rounded-lg shadow-xl max-w-md w-full p-6">
      <div class="flex justify-between items-center mb-4">
        <h2 class="text-xl font-bold text-gray-800">Contact Us</h2>
        <button
          @click="$emit('close')"
          class="text-gray-500 hover:text-gray-700"
        >
          <XIcon class="h-6 w-6" />
        </button>
      </div>

      <!-- Product Details -->
      <div v-if="product" class="mb-6 flex items-center space-x-4">
        <div
          class="w-24 h-24 rounded-md overflow-hidden bg-gray-100 flex-shrink-0"
        >
          <img
            :src="product.image"
            :alt="product.name"
            class="w-full h-full object-cover"
          />
        </div>
        <div>
          <h3 class="font-semibold text-lg text-blue-600">
            {{ product.name }}
          </h3>
          <p class="text-sm text-gray-500">ID: {{ product.id }}</p>
          <div class="mt-1">
            <p class="font-bold text-gray-800">${{ product.priceUSD }}</p>
            <p class="text-sm text-gray-600">
              {{ formatKHR(product.priceKHR) }}
            </p>
          </div>
        </div>
      </div>

      <p class="mb-4 text-gray-600">
        Interested in this product? Contact us through any of these channels:
      </p>

      <div class="space-y-3">
        <ContactLink
          href="tel:069399914"
          icon="phone"
          text="069 399 914"
          bgColor="bg-green-50"
          hoverColor="hover:bg-green-100"
          iconColor="text-green-600"
        />

        <ContactLink
          href="https://www.facebook.com/share/15n9bbHpBM/"
          icon="facebook"
          text="Facebook Page"
          bgColor="bg-blue-50"
          hoverColor="hover:bg-blue-100"
          iconColor="text-blue-600"
          external
        />

        <ContactLink
          :href="telegramLink"
          icon="telegram"
          text="Telegram"
          bgColor="bg-sky-50"
          hoverColor="hover:bg-sky-100"
          iconColor="text-sky-500"
          external
        />

        <ContactLink
          href="https://maps.app.goo.gl/4r3GQdMidp67iU7w6?g_st=ac"
          icon="location"
          text="Store Location"
          bgColor="bg-red-50"
          hoverColor="hover:bg-red-100"
          iconColor="text-red-500"
          external
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from "vue";
import { XIcon } from "lucide-vue-next";
import ContactLink from "./ContactLink.vue";

const props = defineProps({
  show: {
    type: Boolean,
    default: false,
  },
  product: {
    type: Object,
    default: null,
  },
});

defineEmits(["close"]);

// Format KHR price with currency symbol
const formatKHR = (price) => {
  return new Intl.NumberFormat("en-US").format(price) + " ៛";
};

// Create Telegram link with product details
const telegramLink = computed(() => {
  if (!props.product) return "https://t.me/CHHANSOKLAY";

  const message = encodeURIComponent(
    `Hello, I'm interested in this product:\n\n` +
      `Name: ${props.product.name}\n` +
      `ID: ${props.product.id}\n` +
      `Price: $${props.product.priceUSD} / ${formatKHR(
        props.product.priceKHR
      )}\n\n` +
      `Please provide more information about it.`
  );

  return `https://t.me/CHHANSOKLAY?text=${message}`;
});
</script>
