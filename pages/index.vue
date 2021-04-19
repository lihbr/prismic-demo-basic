<!-- HEALTH:HIGH __page__home -->
<template>
  <div
    class="__page__home min-h-screen flex items-center container p-5 mx-auto bg-white shadow-2xl"
  >
    <section class="flex-1 md:flex md:flex-row-reverse">
      <figure class="md:flex-1 md:self-center">
        <prismic-embed
          :field="data.embed"
          class="relative w-full"
          :style="{ paddingBottom: '56.25%' }"
        />
      </figure>
      <article class="flex-1">
        <div class="p-8 flex flex-col h-full justify-between space-y-8">
          <h1 class="text-2xl md:text-4xl leading-snug">
            {{ $prismic.asText(data.title) }}
          </h1>
          <prismic-rich-text :field="data.description" class="space-y-4" />
          <div class="text-center md:text-left">
            <prismic-link
              :field="data.cta_link"
              class="bg-red-500 hover:bg-red-600 transition-colors duration-300 ease-in-out text-white block md:inline-block px-8 py-4 font-bold rounded-lg"
            >
              {{ data.cta_label }}
            </prismic-link>
          </div>
        </div>
      </article>
    </section>
  </div>
</template>

<script>
export default {
  async asyncData({ $prismic }) {
    const { data } = await $prismic.api.getSingle("landing");

    return { data };
  }
};
</script>

<style>
iframe {
  @apply absolute w-full h-full;
}
</style>
