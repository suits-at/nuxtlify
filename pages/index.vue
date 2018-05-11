<template>
  <section class="container">
    <h2>Blog</h2>
    <ul>
      <li v-for="post in posts" :key="post.date">
        <nuxt-link :to="post._path">
          {{ post.title }}
        </nuxt-link>
      </li>
    </ul>
    <h2>Projects</h2>
    <ul>
      <li v-for="project in projects" :key="project.date">
        <nuxt-link :to="project._path">
          {{ project.title }}
        </nuxt-link>
      </li>
    </ul>
    <h2>Services</h2>
    <ul>
      <li v-for="service in services" :key="service.title">
        <nuxt-link :to="service._path">
          {{ service.title }}
        </nuxt-link>
      </li>
    </ul>
  </section>
</template>

<script>
import AppLogo from '~/components/AppLogo.vue';

export default {
  components: {
    AppLogo
  },
  data() {
    // Using webpacks context to gather all files from a folder
    const context = require.context('~/content/blog/posts/', false, /\.json$/);

    const posts = context.keys().map(key => ({
      ...context(key),
      _path: `/blog/${key.replace('.json', '').replace('./', '')}`
    }));

    // Using webpacks context to gather all files from a folder
    const project_context = require.context('~/content/projects/', false, /\.json$/);

    const projects = project_context.keys().map(key => ({
      ...project_context(key),
      _path: `/projects/${key.replace('.json', '').replace('./', '')}`
    }));

    // Using webpacks context to gather all files from a folder
    const service_context = require.context('~/content/services/', false, /\.json$/);

    const services = service_context.keys().map(key => ({
      ...service_context(key),
      _path: `/services/${key.replace('.json', '').replace('./', '')}`
    }));

    return { posts, projects, services };
  }
};
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
