<template>
  <button class="button" @click="aoClicar" :disabled="desabilitado">
      <span class="icon">
        <i :class="icone"></i>
      </span>
      <span>{{ text }}</span>
    </button>
</template>

<script lang="ts">

import { defineComponent } from 'vue'

export default defineComponent({
  name: 'BotaoFormulario',

  emits: ['aoClicar'],

  props: {
    desabilitado: {
      type: Boolean
    },

    icone: {
      type: String,
      required: true,
    },

    text: {
      type: String,
      required: true,
    },
  },

  methods: {
    aoClicar(): void {
      this.$emit('aoClicar')
    }
  }
})

</script>
