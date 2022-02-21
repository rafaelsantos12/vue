<template>
    <div>
      <h1>{{titulo}}</h1>
      <img :src="foto.url" :alt="foto.titulo">

      <ul >
        <li v-for="foto of images">
          <img :src="foto.url" :alt="foto.titulo">
        </li>
      </ul>

    </div>
</template>

<script>
export default {
  data () {

    return {
        titulo: "Hello Word ",
        foto:{
          url: "https://img.freepik.com/fotos-gratis/adoravel-cachorro-basenji-marrom-e-branco-sorrindo-e-dando-mais-uns-cinco-isolado-no-branco_346278-1657.jpg",
          titulo: "Cachoro"
        },
        images:[]
    }
  },

  created(){
      
        this.$http.get('http://localhost:3000/v1/fotos').
        then(res => res.json()).
        then(images => this.images = images, err => console.log(err));
  }
}
</script>

<style>

</style>
