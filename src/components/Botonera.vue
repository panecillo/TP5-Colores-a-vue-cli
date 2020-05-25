<template>

  <section class="src-components-botonera">
    <div id="navitagor">
      <button id="reset" @click="iniciarColores">New Colors!</button>
      <span id="message">{{ mensaje }}</span>
      <button
        id="easy" 
        @click="iniciarEasy"
        :style="{'background-color': colorBotones.botonEasy, 'color': colorBotones.letraEasy}">
      easy
      </button>
      <button
        id="hard"
        @click="iniciarHard"
        :style="{'background-color': colorBotones.botonHard, 'color': colorBotones.letraHard}">
      hard
      </button>

    </div>  
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-botonera',
    props: {
      iniciarColores: Function,
      modificarHard: Function,
      modificarEasy: Function,
      colorBotones: Object,
      mostrarDificultad: Function,
      mensaje: String
    },
    mounted () {
      
    },
    data () {
      return {

      }
    },
    methods: {
      iniciarEasy() {
        if(this.mostrarDificultad() == 6) {
          this.modificarEasy();
          this.iniciarColores();
        }
      },
      iniciarHard() {
        if(this.mostrarDificultad() == 3) {
          this.modificarHard();
          this.iniciarColores();
        }
      }
    },
    computed: {
      
    }
}


</script>

<style scoped lang="css">
  .src-components-botonera {
    text-align: center;
    margin-top: -18px;
    background-color: white;
  }
  #message {
    color: black;
    display: inline-block;
    width: 20%;
  }
  #navigator {
    background: #ffffff;
    height: 30px;
    text-align: center;
    margin: 0;
    margin-top: -30px;
  }
  .selected {
    background-color: steelblue;
    color: white;
  }
  button {
    border: none;
    background-color: white;
    font-family: "Montserrat", "Avenir";
    text-transform: uppercase;
    height: 100%;
    font-weight: 700;
    letter-spacing: 1px;
    color: steelblue;
    transition: all 0.3s;
    outline: none;
    padding:7px
  }
  button:hover {
    color: white;
    background-color: steelblue;
  }
</style>
