<template>
  <article>
    <p> {{ icon }}</p>
    <h2>{{ title }}</h2>
    <vue-markdown> {{ description }} </vue-markdown>
  </article>
</template>

<script>
  import VueMarkdown from 'vue-markdown';
  export default {
  async asyncData({ params }) {
    return await import('~/content/services/' + params.slug + '.json');
  },
  components: {
    VueMarkdown
  }
};
</script>
