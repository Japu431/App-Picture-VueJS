<template>
  <div>
    <h1 class="center">{{ titulo }}</h1>
    <input
      type="search"
      id="filtro"
      class="filtro"
      placeholder="Filtre por parte do título"
      @input="filtro = $event.target.value"
      autocomplete="off"
    />

    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="(foto, i) of fotosComFiltro" :key="i">
        <MeuPainel :titulo="foto.titulo">
          <ImageResponsive :url="foto.url" :titulo="foto.titulo" />
        </MeuPainel>
      </li>
    </ul>
  </div>
</template>

<script>
import Painel from "../shared/painel/Painel.vue";
import ImagemResponsiva from "../shared/imagem-responsive/ImagemResponsiva.vue";

export default {
  components: {
    MeuPainel: Painel,
    ImageResponsive: ImagemResponsiva,
  },

  data() {
    return {
      titulo: "AluraPic",
      fotos: [],
      filtro: "",
    };
  },

  computed: {
    fotosComFiltro() {
      if (this.filtro) {
        let exp = new RegExp(this.filtro.trim(), "i");
        return this.fotos.filter((foto) => exp.test(foto.titulo));
      } else {
        return this.fotos;
      }
    },
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

.lista-fotos {
  list-style: none;
}

.lista-fotos .lista-fotos-item {
  display: inline-block;
}

.filtro {
  display: block;
  width: 100%;
}
</style>
