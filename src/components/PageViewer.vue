<template>
  <div class="page-conatiner">
    <h1 class="main-heading">{{ selectedPage.pageTitle }}</h1>
    <p>This from Page {{ selectedPage.content }}</p>
  </div>
</template>

<script>
export default {
  props: ["selectedPage"],
};
</script>
