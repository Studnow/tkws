<template>
  <div>
    <li v-for="post of posts" :key="post.slug" class="list-none no-underline hover:text-orange-600">
      <NuxtLink :to="post.path">{{ post.title }}</NuxtLink>
    </li>
  </div>
</template>

<script>
export default {
  props: {
    posts: Array,
  }
};
</script>