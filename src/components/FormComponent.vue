<template>
  <div id="form">
    <form @submit.prevent="agregarPaciente">
      <label for="paciente">Paciente</label>
      <input type="text" id="paciente" v-model="nuevoPaciente.nombre">

      <label for="fecha">Fecha</label>
      <input type="date" id="fecha" v-model="nuevoPaciente.fecha">

      <label for="hora">Hora</label>
      <input type="time" id="hora" v-model="nuevoPaciente.hora">

      <label for="gravedad">Gravedad</label>
      <select v-model="nuevoPaciente.gravedad" id="gravedad">
        <option v-for="nivel in nivelGravedad" :key="nivel" :value="nivel">{{ nivel }}</option>
      </select>

      <label for="motivo">Motivo</label>
      <input type="text" id="motivo" v-model="nuevoPaciente.motivo">

      <button type="submit" class="btn-agregar">Agregar</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'FormComponent',
  data() {
    return {
      nivelGravedad: ["baja", "media", "alta"],
      nuevoPaciente: {
        id: '',
        nombre: '',
        fecha: '',
        hora: '',
        gravedad: '',
        motivo: ''
      }
    };
  },
  methods: {
    agregarPaciente() {
      this.$emit('agregar-paciente', { ...this.nuevoPaciente });
      
      // Resetear los campos del formulario
      this.nuevoPaciente = {
        id: '',
        nombre: '',
        fecha: '',
        hora: '',
        gravedad: '',
        motivo: ''
      };
    }
  }
};
</script>

<style scoped>
#form {
  border: 1px solid #ccc;
  padding: 2rem;
  margin: 3rem;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
}

form {
  display: flex;
  align-items: center;
}

form label {
  margin: 0 10px;
  color: #2B3D4F;
  font-weight: bold;
}

form input,
form select {
  margin: 0 10px;
}

.btn-agregar {
  margin: 0 1rem;
  padding: 0.7rem 1.2rem;
  background-color: #91C5F9;
  color:#2B3D4F;
  font-weight: bold;
  border: 1px solid #ccc;
  border-radius: 4px;
  cursor: pointer;
}
</style>
