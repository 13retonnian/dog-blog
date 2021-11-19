<template>
  <v-main>
    <p>my path is {{ $route.path }}</p>
    <v-container>
      <h2>#1 {{ recipe.title }}</h2>
      <nuxt-content :document="recipe" />
    </v-container>
    <v-container>
      <h2>#2 {{ recipe.title }}</h2>
      <p>{{ recipe.description }}</p>
      <nuxt-content :document="recipe" />

      <p>Published date: {{ recipe.date }}</p>
    </v-container>
  </v-main>
</template>
<script>
export default {
  async asyncData({ $content, params, error }) {
    try {
      const recipe = await $content(`recipes/${params.slug}`).fetch()
      return {
        recipe,
      }
    } catch (e) {
      error('No article found')
    }
  },
}
</script>