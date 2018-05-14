<template>
  <article>
    <h2>{{ title }}</h2>
    <vue-markdown> {{ content }} </vue-markdown>
  </article>
</template>

<script>
  import VueMarkdown from 'vue-markdown';
  export default {
  async asyncData({ params }) {
    return await import('~/content/sites/' + params.slug + '.json');
  },
  components: {
    VueMarkdown
  }
};
</script>
