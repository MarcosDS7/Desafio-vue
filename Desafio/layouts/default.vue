<template>
  <div>
    <Nuxt />
  </div>
</template>

<style>

</style>
<script>

import Vue from 'vue';
import Meta from 'vue-meta';

Vue.use(Meta);


export default {
    name: 'App',
    metaInfo: {
      title: 'Desafio | Seja bem mestre!',
      // override the parent template and just use the above title only
      titleTemplate: '%s ← Home',
      htmlAttrs: {
      lang: 'en-US'
    },
    meta: [
      { charset: 'utf-8' },
      { name: 'description', content: 'Aqui você encontra um desafio proposto pelo meu professor!' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' }
    ]
  }
  
}
</script>