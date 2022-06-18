<template>
  <div>
    <li v-for="rootPost of rootPosts" :key="rootPost.slug" class="list-none no-underline hover:text-orange-600">
      <NuxtLink :to="rootPost.path">{{ rootPost.title }}</NuxtLink>
    </li>
  </div>
</template>

<script>
export default {
  props: {
    rootPosts: Array,
  }
};
</script>