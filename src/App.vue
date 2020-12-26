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
      fotos: [
        {
          url:
            "https://www.petz.com.br/blog/wp-content/uploads/2019/04/temperatura-cachorro.jpg",
          titulo: "Cachorro",
        },
        {
          url:
            "https://www.petz.com.br/blog/wp-content/uploads/2019/04/temperatura-cachorro.jpg",
          titulo: "Cachorrão",
        },
      ],
    };
  },
};
</script>

<style

</style>
