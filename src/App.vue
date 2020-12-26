

<template>
  <div class="corpo">
    <h1 class="center">{{ titulo }}</h1>

    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="(foto, i) of fotos" :key="i">
        <MeuPainel :titulo="foto.titulo">
          <img class="image-responsive" :src="foto.url" :alt="foto.titulo" />
        </MeuPainel>
      </li>
    </ul>
  </div>
</template>

<script>
import Painel from "./components/shared/painel/Painel.vue";
export default {
  components: {
    MeuPainel: Painel,
  },

  data() {
    return {
      titulo: "AluraPic",
      fotos: [],
      filtro: "",
    };
  },
  created() {
    let promise = this.$http.get("http://localhost:3000/v1/fotos");

    promise
      .then((res) => res.json())
      .then((fotos) => (this.fotos = fotos))
      .catch((err) => console.log(err));
  },
};
</script>

<style scoped>
.center {
  text-align: center;
}

.corpo {
  font-family: Helvetica, sans-serif;
  margin: 0 auto;
  width: 96%;
}

.lista-fotos {
  list-style: none;
}

.lista-fotos .lista-fotos-item {
  display: inline-block;
}

.image-responsive {
  width: 100%;
}

.filtro {
  display: block;
  width: 100%;
}
</style>
