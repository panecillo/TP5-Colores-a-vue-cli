<template>

  <section class="src-components-contenedor">
    <div id="container">
      <div v-for="(color, index) in colores" :key="index">
        <Cuadrado 
          :color="color"
          :colorAJugar="colorAJugar"
          :index="index"
          :ganador="ganador"
          :activador="activador"
          @actualizar-color="actualizarColor($event)"
        />
      </div>
    </div>
  </section>

</template>

<script lang="js">

  import Cuadrado from './Cuadrado.vue'

  export default  {
    name: 'src-components-contenedor',
    props: {
      colores: Array,
      colorAJugar: String,
      ganador: Function,
      activador: String
    },
    components: {
      Cuadrado
    },
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {
      actualizarColor(obj) {
        this.$emit('actualizar-color', obj)
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-contenedor {
    background: black;
  }
  #container {
    background: black;
  }
</style>
