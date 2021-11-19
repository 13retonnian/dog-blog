<template>
  <div>
    <section>
      <h2>Articles</h2>
      <nav>
        <ul>
          <li v-for="post in posts" :key="post.slug">
            <NuxtLink :to="`blog/${post.slug}`"> {{ post.title }}</NuxtLink>
          </li>
        </ul>
      </nav>
    </section>
    <v-container>
      <h2>Recipes</h2>
      <ul>
        <li v-for="recipe in recipes" :key="recipe.slug">
          <NuxtLink :to="`recipes/${recipe.slug}`">
            {{ recipe.title }}</NuxtLink
          >
        </li>
      </ul>
    </v-container>
  </div>
</template>
<script>
export default {
  // fetch the data from the blog in the content folder
  async asyncData({ $content }) {
    const posts = await $content('blog').fetch()
    const recipes = await $content('recipes').fetch()

    return {
      posts,
      recipes,
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
