<template>
  <div class="container bg-dark">
    <h1 class="bg-primary">Movies</h1>
    <article class="card">
      {{ item.title ? item.title : item.name }}
    </article>
  </div>
</template>

<script>
export default {
  name: "MyCard",
  props: {
    item: Object,
  },
};
</script>

<style></style>
