<template>
  <article>
    <h1>{{ title }}</h1>
    <p>created: {{ date }}</p>
    <vue-markdown>{{ body }}</vue-markdown>
    <img :src="thumbnail"/>

  </article>
</template>

<script>
  import VueMarkdown from 'vue-markdown';

  export default {
    async asyncData({params}) {
      return await import('~/content/blog/posts/' + params.slug + '.json');
    },
    components: {
      VueMarkdown
    }
  };
</script>
