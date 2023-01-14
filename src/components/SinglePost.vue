<template>
  <div class="post">
    <router-link :to="{ name: 'Details', params: { id: post.id } }">
      <h3>{{ post.title }}</h3>
    </router-link>

    <p>{{ snippet }}</p>

    <span v-for="tag in post.tags" :key="tag">#{{ tag }}</span>
  </div>
</template>

<script>
import { computed, onMounted, onUnmounted, onUpdated } from "@vue/runtime-core";

export default {
  props: ["post"],
  setup(props) {
    onMounted(() => console.log("mounted"));
    onUnmounted(() => console.log("unmounted"));
    onUpdated(() => console.log("updated"));

    const snippet = computed(() => {
      return props.post.body.substring(0, 100) + "....";
    });

    return { snippet };
  },
};
</script>

<style>
</style>