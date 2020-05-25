<template>

  <section class="src-components-cuadrado">
    <div class="square"
      :style="{'background-color': color}"
      @click="mostrarColor"
    >{{activador}}
    </div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-cuadrado',
    props: {
      color: String,
      colorAJugar: String,
      index: Number,
      ganador: Function,
      activador: String
    },
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {
      mostrarColor() {
        if(this.color != this.colorAJugar){
          let obj = {
            color: "#232323",
            index: this.index
          }
          this.$emit('actualizar-color', obj)
          this.ganador(false)
        }
        else {
          this.ganador(true)
        }
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-cuadrado {
    
  }
  .square {
    width: 30%;
    padding-bottom: 30%;
    float: left;
    margin: 1.66%;
    border-radius: 10%;
    transition: background 0.8s;
    -webkit-transition: background 0.8s;
    -moz-transition: background 0.8s;
  }

</style>
