<template>
  <div>
    <li v-for="som of some" :key="som.slug" class="list-none no-underline hover:text-orange-600">
      <NuxtLink :to="som.path">{{ som.title }}</NuxtLink>
    </li>
    <!-- <span>{{$content(params.slug)}}</span> -->
  </div>
</template>

<script>
export default {
  props: {
    some: Array,
  }
};
</script>