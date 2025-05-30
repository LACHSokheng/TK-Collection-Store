<template>
  <a
    :href="href"
    :target="external ? '_blank' : undefined"
    :rel="external ? 'noopener noreferrer' : undefined"
    :class="[
      'flex items-center space-x-3 p-3 rounded-lg transition-colors',
      bgColor,
      hoverColor,
    ]"
  >
    <component :is="iconComponent" :class="['h-6 w-6', iconColor]" />
    <span class="text-gray-800">{{ text }}</span>
  </a>
</template>

<script setup>
import { computed } from "vue";
import { PhoneIcon, MapPinIcon } from "lucide-vue-next";
import FacebookIcon from "./icons/FacebookIcon.vue";
import TelegramIcon from "./icons/TelegramIcon.vue";

const props = defineProps({
  href: {
    type: String,
    required: true,
  },
  icon: {
    type: String,
    required: true,
  },
  text: {
    type: String,
    required: true,
  },
  bgColor: {
    type: String,
    default: "bg-gray-50",
  },
  hoverColor: {
    type: String,
    default: "hover:bg-gray-100",
  },
  iconColor: {
    type: String,
    default: "text-gray-600",
  },
  external: {
    type: Boolean,
    default: false,
  },
});

const iconComponent = computed(() => {
  const iconMap = {
    phone: PhoneIcon,
    facebook: FacebookIcon,
    telegram: TelegramIcon,
    location: MapPinIcon,
  };
  return iconMap[props.icon] || PhoneIcon;
});
</script>
