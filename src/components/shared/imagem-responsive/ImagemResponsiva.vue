<template>
  <img class="image-responsive" :src="url" :alt="titulo" />
</template>

<script>
export default {
  props: ["url", "titulo"],
};
</script>

<style scoped>

.image-responsive {
  width: 100%;
}

</style>


