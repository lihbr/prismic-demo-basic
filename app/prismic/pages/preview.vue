<!-- HEALTH:HIGH __page__preview -->
<template>
  <div
    class="__page__preview min-h-screen flex items-center justify-center container p-5 mx-auto"
  >
    <h1 class="font-bold text-2xl md:text-4xl leading-snug text-orange-600">
      Loading Prismic preview...
    </h1>
  </div>
</template>

<script>
export default {
  mounted() {
    this.$prismic.preview();
  }
};
</script>
