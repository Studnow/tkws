<template>
  <!-- <Tutorial :posts="posts"/> -->
  <div id="app">
    <Header />
    <div class="mx-auto flex mt-8">
      <div class="blog mx-auto">
        <h3 class="font-bold text-xl">Links from blog collection</h3>
        <PostList :posts="posts" />
      </div>
      <div class="some mx-auto">
        <h4 class="font-bold text-xl">Links from some collection</h4>
        <SomeList :some="some" />
      </div>
      <div class="some mx-auto">
        <h4 class="font-bold text-xl">Links from Root collection</h4>
        <Root :rootPosts="rootPosts" />
      </div>
    </div>
    <NuxtContent class="mt-8" :document="doc" />
    <!-- <NuxtContent :document="some" /> -->
  </div>
</template>

<script>
import Header from '~/components/Header.vue'
export default {
  name: 'IndexPage',
  head() {
    return {
      script: [
        { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' },
      ],
    }
  },
  async asyncData({ $content }) {
    const posts = await $content('blog').fetch()
    const doc = await $content('hello').fetch()
    const some = await $content('some').fetch()
    const rootPosts = await $content('pages/blog').fetch()
    return {
      posts,
      doc,
      some,
      rootPosts
    }
  },
  // async asyncData({ $content }) {
  //     const doc = await $content("hello").fetch();
  //     return {
  //         doc,
  //     };
  // },
  components: { Header },
}
</script>
