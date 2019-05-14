<template>
  <div id="app">
     <v-header :seller="seller"></v-header>
  </div>
</template>

<script>
import {urlParse} from './common/js/util';
import header from './components/header/header.vue'
const response=require('./common/data/seller.json');
const ERR_OK = 0;
export default {
  // name: 'App',
  data(){
      seller: {
          id: (() => {
            let queryParam = urlParse();
            return queryParam.id;
          })()
      }
  },
  components: {
     'v-header':header
  },
  created(){
        if (response.errno === ERR_OK) {
          this.seller = Object.assign({}, this.seller, response.data);
        }
  }
}
</script>

<style>

</style>
