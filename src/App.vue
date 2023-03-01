<template>
  <main class="columns is-gapless is-multiline modo-escuro">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>

    <div class="column is-three-quarter conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefa" />

      <div class="lista">
        <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        <Box v-if="listaEstaVazia">
          Você não está muito produtivo hoje :(
        </Box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">

import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Formulario from './components/Formulario.vue';
import Tarefa from './components/Tarefa.vue';
import { ITarefa } from './interfaces/ITarefa'
import Box from './components/Box.vue';

export default defineComponent({
  name: "App",

  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box
},

  data () {
    return {
      tarefas: [] as ITarefa[]
    }
  },

  computed: {
    listaEstaVazia (): boolean {
      return this.tarefas.length < 1
    }
  },

  methods: {
    salvarTarefa (tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    }
  },
});

</script>

<style>

main {
  --bg-primario: #FFF;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2B2D42;
  --texto-primario: #DDD;
}

.conteudo {
  background-color: var(--bg-primario);
}

.lista {
  padding: 1.25rem;
}

</style>
