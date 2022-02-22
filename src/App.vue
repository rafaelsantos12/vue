<template>
    <div class="corpo">
      <h1 class="titulo">{{titulo}}</h1>
      <img :src="foto.url" :alt="foto.titulo">

      <ul  class="lista-foto">
        <li class="lista-fotos-item" v-for="foto of images" v-bind:key="foto._id">
          
          <div class="painel">
            <h2 class="painel-titulo">{{foto.titulo}}</h2>
            <div class="painel-corpo"> 
                <img class="imagem-responsivo" :src="foto.url" :alt="foto.titulo">
            </div>
          </div>
   
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
  .corpo{
    font-family: Helvetica, sans-serif;
    width: 96%;
    margin: 0 auto;
  }

  .titulo{
    text-align: center;
  }

  .lista-foto{
    list-style: none;
  }

  .lista-fotos-item{
    display: inline-block;
    margin: 10px 5px;
  }

    .imagem-responsivo{
      width: 100% ;
    }
    /* estilo do painel */ 

   .painel {
    padding: 0 auto;
    border: solid 2px grey;
    display: inline-block;
    margin: 5px;
    box-shadow: 5px 5px 10px grey;
    width: 200px;
    height: 100%;
    vertical-align: top;
    text-align: center;
  }

  .painel .painel-titulo {
    text-align: center;
    border: solid 2px;
    background: lightblue;
    margin: 0 0 15px 0;
    padding: 10px;
    text-transform: uppercase;
  }
</style>
