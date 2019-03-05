<template lang="html">
  <div class="row">
    <div class="col-sm-12">
      <h3 class="text-center">Citas añadidas</h3>
      <div class="progress">
        <!-- Calculamos el ancho con la siguiente división -->
        <div class="progress-bar" role="progressbar" aria-valuenow="60" 
        aria-valuemin="0" aria-valuemax="100" :style="{width: (quoteCount / maxQuotes) *100 + '%'}">
          {{quoteCount}} / {{maxQuotes}}
        </div>
    </div>
  </div>
</div>	

</template>

<script lang="js">
  export default  {
    name: 'header',
    props: ['quoteCount', 'maxQuotes'],
    mounted() {

    },
    data() {
      return {

      }
    },
    methods: {

    },
    computed: {

    }
}
</script>

<style scoped lang="css">
</style>
