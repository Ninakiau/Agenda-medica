<script>
export default {
  name: 'Formulario',
  data() {
    return {
      localNombre: '',
      localFecha: '',
      localHora: '',
      localGravedad: '',
      localMotivo: ''
    };
  },
  methods: {
    agregar(event) {
      event.preventDefault();
      if (this.validarCampos()) {
        const nuevaCita = {
          nombre: this.localNombre,
          fecha: this.localFecha,
          hora: this.localHora,
          gravedad: this.localGravedad,
          motivo: this.localMotivo
        };
        this.$emit('nueva-cita', nuevaCita);
        this.limpiarCampos();
      }
    },
    limpiarCampos() {
      this.localNombre = '';
      this.localFecha = '';
      this.localHora = '';
      this.localGravedad = '';
      this.localMotivo = '';
    },
    validarCampos() {
      if (
        this.localNombre === '' ||
        this.localFecha === '' ||
        this.localHora === '' ||
        this.localGravedad === '' ||
        this.localMotivo === ''
      ) {
        alert('Por favor, rellene todos los campos');
        return false;
      }
      return true;
    }
  }
};
</script>

<template>
  <div>
    <form @submit="agregar" class="container">
      <div class="form">
        <div class="form-group">
          <label for="nombre">Paciente</label>
          <input type="text" v-model="localNombre" id="nombre">
        </div>
        <div class="form-group">
          <label for="fecha">Fecha</label>
          <input type="date" v-model="localFecha" id="fecha">
        </div>
        <div class="form-group">
          <label for="hora">Hora</label>
          <input type="time" v-model="localHora" id="hora">
        </div>
        <div class="form-group">
          <label for="gravedad">Gravedad</label>
          <select v-model="localGravedad" id="gravedad">
            <option value="baja">Baja</option>
            <option value="media">Media</option>
            <option value="alta">Alta</option>
          </select>
        </div>
        <div class="form-group">
          <label for="motivo">Motivo</label>
          <textarea v-model="localMotivo" id="motivo" cols="30" rows="3"></textarea>
        </div>
      </div>
      <button type="submit">Agregar</button>
    </form>
  </div>
</template>

<style scoped>
.form {
  display: flex;
  flex-direction: row;
  gap: 1rem;
  justify-content: space-around;
  align-items: start;
}
.form-group {
  display: flex;
  flex-direction: column;
  gap: .5rem;
}
.container {
  box-shadow: 0 0 1rem 0 rgba(0, 0, 0, 0.2);
  padding: 2rem;
  border-radius: .5rem;
  border-style: solid;
  border-color: rgb(163, 163, 163);
  border-width: 1px;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  align-items: center;
}
label {
  color: red;
  font-weight: bolder;
  align-self: center;
}
</style>
