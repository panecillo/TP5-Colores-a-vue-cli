<template>

  <section class="src-components-juego">
    <div id="body">
      <Cabecera
        :colorGanador="colorGanador"
        :colorAJugar="colorAJugar"
      />
      <Botonera
        :iniciarColores="iniciarColores"
        :modificarHard="modificarHard"
        :modificarEasy="modificarEasy"
        :colorBotones="colorBotones"
        :mostrarDificultad="mostrarDificultad"
        :mensaje="mensaje"
      />
      <Contenedor
        :colores="colores"
        :colorAJugar="colorAJugar"
        :ganador="ganador"
        :activador="activador"
        @actualizar-color="actualizarColor($event)"
      />
    </div>
  </section>

</template>

<script lang="js">

  import Cabecera from './Cabecera.vue'
  import Botonera from './Botonera.vue'
  import Contenedor from './Contenedor.vue'

  export default  {
    name: 'src-components-juego',
    props: [],
    components : {
      Cabecera,
      Botonera,
      Contenedor
    },
    mounted () {
      this.iniciarColores();
      console.log("El color a jugar es: " + this.colorAJugar)
      console.log(this.colores)
      console.log("El color a jugar es: " + this.colorAJugar)
    },
    data () {
      return {
        colorGanador: 'steelblue',
        colorAJugar: "",
        colores: [],
        hard: 6,
        easy: 3,
        dificultad: 6,
        colorBotones : {
          botonEasy: "rgb(251, 251, 251)",
          botonHard: "rgb(70, 130, 180)",
          letraEasy: "rgb(70, 130, 180)",
          letraHard: "rgb(251, 251, 251)"
        },
        mensaje: "",
        activador: ""
      }
    },
    methods: {
      iniciarColores() {
        this.colores = []
        this.colorGanador = 'steelblue'
        this.mensaje = ""
        for(var i = 0; i < this.dificultad; i++){
          this.colores[i] = this.generarStringColor();
        }
        this.colorAJugar = this.generarColorAJugar(this.dificultad)
      },
      mostrarDificultad() {
        return this.dificultad
      },
      modificarHard() {
        this.dificultad = this.hard;
        this.colorBotones.botonEasy = "rgb(251, 251, 251)";
        this.colorBotones.botonHard = "rgb(70, 130, 180)";
        this.colorBotones.letraEasy = "rgb(70, 130, 180)";
        this.colorBotones.letraHard = "rgb(251, 251, 251)";
      },
      modificarEasy() {
        this.dificultad = this.easy;
        this.colorBotones.botonEasy = "rgb(70, 130, 180)";
        this.colorBotones.botonHard = "rgb(251, 251, 251)";
        this.colorBotones.letraEasy = "rgb(251, 251, 251)";
        this.colorBotones.letraHard = "rgb(70, 130, 180)";
      },
      generarStringColor() {
        return "rgb(" + this.generarInt() + ", " + this.generarInt() + ", " + this.generarInt() + ")"
      },
      generarInt() {
        return Math.floor(Math.random() * 256);
      },
      generarColorAJugar(dificultad) {
        return this.colores[Math.floor(Math.random() * (dificultad - 1))]
      },
      actualizarColor(obj) {
        this.colores.splice(obj.index, 1, obj.color)

      },
      ganador(resultado) {
        if(resultado) {
          this.colorGanador = this.colorAJugar
          this.mensaje = "Ganaste!"
          let coloresGanadores = []
          for (let index = 0; index < this.colores.length; index++) {
            coloresGanadores[index] = this.colorGanador
          }
          this.colores = coloresGanadores
        }
        else {
          this.mensaje = "Inténtalo de nuevo!"
        }
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-juego {
    background: #232323;
  }

  #body {
    background: #232323;
    margin: 0;
    font-family: "Montserrat", "Avenir";
  }
</style>
