<template>
  <article>
    <h1>{{ title }}</h1>
    <p> {{ date }}</p>
    <p> {{url}} </p>
    <img :src="screenshot"/>
  </article>
</template>

<script>
export default {
  async asyncData({ params }) {
    return await import('~/content/projects/' + params.slug + '.json');
  }
};
</script>
