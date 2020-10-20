<!-- HEALTH:HIGH __page__home -->
<template>
  <div
    class="__page__home min-h-screen flex items-center container p-5 mx-auto"
  >
    <section
      class="md:flex md:items-stretch rounded-lg overflow-hidden shadow-2xl bg-white"
    >
      <picture class="flex-1">
        <prismic-image :field="data.image" class="object-cover h-full w-full" />
      </picture>
      <article class="flex-1">
        <div class="p-8 flex flex-col h-full justify-between space-y-8">
          <div class="space-y-8">
            <h1
              class="font-bold text-2xl md:text-4xl leading-snug text-orange-600"
            >
              {{ $prismic.asText(data.title) }}
            </h1>
            <prismic-rich-text :field="data.description" />
          </div>
          <div class="text-center md:text-right">
            <prismic-link
              :field="data.cta_link"
              class="bg-orange-600 hover:bg-orange-700 transition-colors duration-300 ease-in-out text-white block md:inline-block px-8 py-4 font-bold rounded-lg"
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
    const data = (await $prismic.api.getSingle("landing")).data;

    return { data };
  },
  head() {
    const { meta_title, meta_description } = this.data;

    const head = {
      meta: []
    };

    if (meta_title) {
      head.title = meta_title;
    }

    if (meta_description) {
      head.meta.push({
        hid: "description",
        name: "description",
        content: meta_description
      });
    }

    return head;
  }
};
</script>

<style></style>
