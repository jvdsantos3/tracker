<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempoEmSegundos="tempoEmSegundos" />

    <button class="button" @click="iniciar" :disabled="cronometoRodando">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!cronometoRodando">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">

import { defineComponent } from 'vue'
import Cronometro from './Cronometro.vue'

export default defineComponent({
  name: 'TemporizadorTarefa',

  components: {
    Cronometro,
  },

  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometoRodando: false
    };
  },

  methods: {
    iniciar() {
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1;
      }, 1000);

      this.cronometoRodando = true
    },

    finalizar() {
      clearInterval(this.cronometro);

      this.cronometoRodando = false
    }
  },
})

</script>