<template>
  <div>
    <h1>{{ titulo }}</h1>
    <ul>
      <li v-for="(foto, i) of fotos" :key="i">
        <img :src="foto.url" :alt="foto.titulo" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titulo: "AluraPic",
      fotos: [],
    };
  },
  created() {
    let promise = this.$http.get("http://localhost:3000/v1/fotos");
    promise
    .then(res => res.json())
    .then(fotos => this.fotos = fotos)
    .catch(err => console.log(err))
  },
};
</script>

<style>
</style>
