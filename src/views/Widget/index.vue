<template>
  <teleport to="body">
    <component
      @open-box="handleOpenBox"
      @close-box="handleCloseBox"
      :is="state.component"
    />
  </teleport>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue'
import Standby from './Standby.vue'
import Box from './Box.vue'

type State = {
  component: string;
}

interface SetupReturn {
  state: State;
  handleCloseBox(): void;
  handleOpenBox(): void;
}

export default defineComponent({
  components: {
    Standby,
    Box
  },

  setup (): SetupReturn {
    const state = reactive<State>({
      component: 'Standby'
    })

    function handleOpenBox () {
      state.component = 'Box'
    }

    function handleCloseBox () {
      state.component = 'Standby'
    }

    return {
      state,
      handleOpenBox,
      handleCloseBox
    }
  }
})
</script>

<style>

</style>
