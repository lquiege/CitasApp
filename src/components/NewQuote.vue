<template lang="html">

  <div class="row">
    <form action="">
      <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-sm-offset-3">

        <label>Cita</label>
        <textarea class="form-control" name="" id="" cols="30" rows="3" v-model="quote"></textarea>
      </div>
      <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-sm-offset-3">
       
        <button class="btn btn-primary" @click.prevent="createNew" :disabled="disabled">Añadir cita</button>
      </div>
    </form>
    
  </div>

</template>

<script lang="js">
  import {eventBus} from '../main';
  export default  {
    name: 'newQuote',
    data(){
      return {
        quote: ''
      }
    },
    methods:{
      createNew(){
       //   this.$emit('quoteAdded', this.quote);
          eventBus.$emit('quoteAdded', this.quote);
          this.quote = '';
      }

    },

    computed: {
      disabled(){
        return this.quote.length==0 ? true : false
      }
    },

}
</script>

<style scoped lang="css">
div {
  margin-top: 10px;
  margin-bottom: 10px;
}
</style>
