<template>
  <div id="app">
    <Formulario @nueva-cita="agregar" />
    <div class="cards-container">
      <Card
        v-for="(cita, index) in citas"
        :key="index"
        :nombre="cita.nombre"
        :fecha="cita.fecha"
        :hora="cita.hora"
        :gravedad="cita.gravedad"
        :motivo="cita.motivo"
        @eliminar-cita="eliminar(index)"
      />
    </div>
  </div>
</template>

<script>
import Formulario from './components/Formulario.vue';
import Card from './components/Card.vue';

export default {
  name: 'App',
  components: {
    Formulario,
    Card
  },
  data() {
    return {
      citas: []
    };
  },
  methods: {
    agregar(cita) {
      this.citas.push(cita);
    },
    eliminar(index) {
      this.citas.splice(index, 1);
    }
  }
};
</script>

<style scoped>
#app {
  text-align: center;
}

.cards-container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
  margin-top: 2rem;
}
</style>
