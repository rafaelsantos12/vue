<template>
    <div class="corpo">
      <h1 class="titulo">{{titulo}}</h1>
      <!-- <img :src="foto.url" :alt="foto.titulo"> -->
      <input type="search" class="filtro" v-on:input="filtro = $event.target.value" placeholder="Digite aqui nome da foto"/>
      {{filtro}}
      <ul  class="lista-foto">
        <li class="lista-fotos-item" v-for="foto of images" v-bind:key="foto._id">
          
          <Painel  :titulo="foto.titulo">
            <img class="imagem-responsivo" :src="foto.url" :alt="foto.titulo">
          </Painel>
           
   
        </li>
      </ul>

    </div>
</template>

<script>
import Painel from './components/shared/painel/Painel.vue';
export default {
  
  components:{
    'Painel': Painel
  },

  data () {

    return {
        titulo: "Hello Word ",
        foto:{
          url: "https://img.freepik.com/fotos-gratis/adoravel-cachorro-basenji-marrom-e-branco-sorrindo-e-dando-mais-uns-cinco-isolado-no-branco_346278-1657.jpg",
          titulo: "Cachoro"
        },
        images:[],
        filtro:''
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

</style>
