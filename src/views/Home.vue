<template>
  <div class="home">
    <input type="text"
      id="porta"
      placeholder="Porta"
      v-model="porta"
    /> : 
    <input type="text"
      id="url"
      v-model="url"
      placeholder="Dev Url"
    />
    <button @click="parseUrl(porta, url)">Enviar</button>

  </div>

  <Browser :url="urlPronta"/>
    
</template>

<script>

import Browser from '@/components/Browser'

const { port } = require('../../config.json')

export default {
  name: 'Home',
  components: {
    Browser
  },
  data() {
    return {
      porta: null,
      url: null,
      urlPronta: '',
    }
  },
  methods: {
    parseUrl(porta, url) {
      this.urlPronta = `http://localhost:${porta == null ? port : porta}/${url == null ? '' : url}`
    },
  }
}
</script>

<style>
  .home {
    width: 100%;
    display: flex;
    margin-bottom: 10px;
    padding: 10px;
    -webkit-app-region: drag;
  }
  #porta {
    width: 25%;
  }

  #url {
    width: 55%;
    margin-right: 12px;
  }

  input {
    border: 2px solid black;
    outline: none;

    border-radius: 9px;

    padding-left: 9px;

    font-weight: 500;
    -webkit-app-region: none;
  }

  button {
    
    -webkit-app-region: none;
  }
</style>

