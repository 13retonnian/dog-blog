<template>
  <article>
    <h2>{{ post.title }}</h2>
    <nuxt-content :document="post" />
    <p>This is easy once you get the hang of it.</p>
  </article>
</template>
<script>
export default {
  async asyncData({ $content, params, error }) {
    try {
      const post = await $content(`blog/${params.slug}`).fetch()
      return {
        post,
      }
    } catch (error) {
      error('No article found')
    }
  },
}
</script>