<template>
  <v-app>
    <v-main>
      <Evento/>
    </v-main>
  </v-app>
</template>

<script>

import Evento from './components/Evento.vue';

export default {
  name: 'App',

  components: {
    Evento
  },

  data: () => ({
    //
  }),
}
</script>
