<!-- HEALTH:HIGH __page__home -->
<template>
  <div
    class="__page__home min-h-screen flex items-center container p-5 mx-auto bg-white shadow-2xl"
  >
    <section class="md:flex md:flex-row-reverse">
      <figure class="md:flex-1 md:self-center">
        <div class="relative w-full" :style="{ paddingBottom: '56.25%' }">
          <iframe
            width="560"
            height="315"
            src="https://www.youtube.com/embed/G6J2kl1aVao"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
          ></iframe>
        </div>
      </figure>
      <article class="flex-1">
        <div class="p-8 flex flex-col h-full justify-between space-y-8">
          <h1 class="text-2xl md:text-4xl leading-snug">
            JavaScript Array Map Method Practice in 5 Minutes
          </h1>
          <p>
            Arrays are an essential part of <em>JavaScript</em>. If you want to
            get better at JavaScript, you have to know how to effectively use
            arrays, especially the built-in array methods like map, reduce,
            filter, sort, every, some, etc. In this series, we'll cover the
            JavaScript array methods you <strong>need</strong> to know to become
            a web developer.
          </p>
          <p>Learn to use the Map() function to transform items in an array.</p>
          <div class="text-center md:text-left">
            <a
              href="https://www.youtube.com/watch?v=3LOEGS4qcRM&list=PLDlWc9AfQBfZGZXFb_1tcRKwtCavR7AfT"
              class="bg-red-500 hover:bg-red-600 transition-colors duration-300 ease-in-out text-white block md:inline-block px-8 py-4 font-bold rounded-lg"
              target="_blank"
              rel="noopener"
            >
              Discover Similar Courses
            </a>
          </div>
        </div>
      </article>
    </section>
  </div>
</template>

<script>
export default {};
</script>

<style>
iframe {
  @apply absolute w-full h-full;
}
</style>
