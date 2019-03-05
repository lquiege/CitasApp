<template lang="html">

  <div class="row">
     <!-- con el modificador native permitimos el evento click en un componente, y lo que pasamos 
     entre corchetes es el contenido del slot  -->
    <app-quote v-for="(quote, index) in quotes" @click.native="deleteQuote(index)">{{quote}}</app-quote>
  </div>

</template>

<script lang="js">
  import {eventBus} from '../main';
  import Quote from './Quote.vue';
  export default  {
    name: 'quoteGrid',
    props: {
      quotes : {
        type: Array
      }
    },
    components: {
      appQuote: Quote
    },
    
    data() {
      return {

      }
    },
    methods: {
      deleteQuote(index){
        eventBus.$emit('deleteQuote', index);
      }
    }
}
</script>

<style scoped lang="css">
</style>
