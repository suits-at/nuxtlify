<template>
  <article>
    <h1>{{ title }}</h1>
    <p>created: {{ date }}</p>
    <p>{{ body }}</p>
    <img :src="thumbnail" />

  </article>
</template>

<script>
export default {
  async asyncData({ params }) {
    return await import('~/content/projects/project/' + params.slug + '.json');
  }
};
</script>
