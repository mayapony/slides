<script setup>
const props = defineProps({
  image: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <div class="slidev-layout h-full grid">
    <div class="flex flex-grow flex-col">
      <div class="flex flex-col justify-start flex-grow">
        <slot />
      </div>
      <div
        class="w-full flex justify-center items-center p-2 max-h-sm object-cover"
      >
        <img
          :src="image"
          class="rounded-2xl border-image h-full object-cover"
        />
      </div>
    </div>
    <Footer />
  </div>
</template>
