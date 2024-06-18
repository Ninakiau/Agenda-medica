<script>
export default {
  name: 'Card',
  props: {
    nombre: String,
    fecha: String,
    hora: String,
    gravedad: String,
    motivo: String
  },
  methods: {
      eliminar(){
          this.$emit('eliminar-cita', this.index)
      }
  }
};
</script>

<template>
  <div :class="{ card: true, red: gravedad === 'alta', green: gravedad === 'baja', yellow: gravedad === 'media'}">
    <div class="card-body">
      <h5 class="card-title">Paciente</h5>
      <p class="card-text">{{ nombre }}</p>
      <h5 class="card-title">Fecha</h5>
      <p class="card-text">{{ fecha }}</p>
      <h5 class="card-title">Hora</h5>
      <p class="card-text">{{ hora }}</p>
      <h5 class="card-title">Motivo</h5>
      <p class="card-text">{{ motivo }}</p>
      <button @click="eliminar">Eliminar</button>
    </div>
  </div>
</template>

<style scoped>
.card {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: .5rem;
  width: 10rem;
  height: auto;
  padding-bottom: .8rem;
}

.red {
  background-color: red;
}

.green {
  background-color: green;
}
.yellow {
  background-color: yellow;
}

</style>
