<template>
  <div>
    <h2>{{ article.title }}</h2>
    <nuxt-content :document="article" />
  </div>
</template>

<script>
export default {
  async asyncData ({ $content, app, params, error }) {
    const path = `/${params.pathMatch || 'index'}`
    const [article] = await $content({ deep: true }).where({ path }).fetch()
    if (!article) {
      return error({ statusCode: 404, message: 'Article not found' })
    }
    return {
      article
    }
  }
}
</script>