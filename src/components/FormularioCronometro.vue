<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Formulário para criação de nova tarefa">
        <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?">
      </div>
      <div class="column">
        <div class="is-flex is-align-items-center is-justify-content-space-between">
          <section>
          <strong>{{ tempoDecorrido }}</strong>
        </section>
        <button class="button" @click="iniciar">
          <span class="icon">
            <i class="fas fa-play"></i>
          </span>
          <span>play</span>
        </button>
        <button class="button" @click="finalizar">
          <span class="icon">
            <i class="fas fa-stop"></i>
          </span>
          <span>stop</span>
        </button>
        </div>

      </div>
    </div>
  </div>

</template>

<script lang="ts">
/* data são os dados que o componente armazena e computed é uma propriedade que fica verificando quando um dado muda executa uma funcao*/
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'FormularioCronometro',
  data(){
    return{
      tempoEmSegundos:0,
      cronometro: 0
    }
  },
  computed:{
    tempoDecorrido(){
      return new Date(this.tempoEmSegundos * 1000).toISOString().substring(11,19);
    }
  },
  methods:{
    iniciar(){
      this.cronometro = setInterval(()=>{
        console.log("Incrementando")
        this.tempoEmSegundos+=1
      },1000)
      console.log("iniciando")
    },
    finalizar(){
      console.log("iniciando")
      clearInterval(this.cronometro)
      this.zerarCronometro()
    },
    zerarCronometro(){
      this.tempoEmSegundos=0;
    }
  }
})
</script>
