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

      <p class="mb-4 text-gray-600">
        Interested in
        <span class="font-semibold text-blue-600">{{ product?.name }}</span
        >? Contact us through any of these channels:
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
          href="https://t.me/mesokheng"
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
import { XIcon } from "lucide-vue-next";
import ContactLink from "./ContactLink.vue";

defineProps({
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
</script>
