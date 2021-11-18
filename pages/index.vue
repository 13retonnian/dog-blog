<template>
  <div>
    <section>
      <h2>Articles</h2>
      <nav>
        <ul>
          <li v-for="post in posts" :key="post.slug">
            <NuxtLink :to="post.slug"> {{ post.title }}</NuxtLink>
          </li>
        </ul>
      </nav>
    </section>
  </div>
</template>
<script>
export default {
  // fetch the data from the blog in the content folder
  async asyncData({ $content }) {
    const posts = await $content('blog').fetch()
    return {
      posts,
    }
  },
  head() {
    return {
      script: [
        { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' },
      ],
    }
  },
}
</script>
