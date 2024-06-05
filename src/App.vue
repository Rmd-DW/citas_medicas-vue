<template>
  <div id="app">
    <h1>Citas médicas</h1>
    <FormComponent @agregar-paciente="agregarPaciente" />
    <ListaPacientes 
      :listaPacientes="listaPacientes"
      @eliminar-paciente="eliminarPaciente" 
    />
  </div>
</template>

<script>
import FormComponent from './components/FormComponent';
import ListaPacientes from './components/ListaPacientes';

export default {
  name: 'App',
  components: {
    FormComponent,
    ListaPacientes
  },
  data() {
    return {
      listaPacientes: [
        // { id: 1, nombre: 'Juan Villaseca', fecha: '06/05/2024', hora: '07:53', gravedad: 'alta', motivo: 'accidente vehicular' },
        // { id: 2, nombre: 'Felipe Lobos', fecha: '25/10/2024', hora: '10:00', gravedad: 'media', motivo: 'corte maquina' },
        // { id: 3, nombre: 'Claudio Gonzalez', fecha: '11/03/2024', hora: '12:30', gravedad: 'baja', motivo: 'corte maquina' }
      ]
    }
  },
  methods: {
    agregarPaciente(paciente) {
    
      const nuevoId = this.listaPacientes.length ? Math.max(...this.listaPacientes.map(p => p.id)) + 1 : 1;
      this.listaPacientes.push({ ...paciente, id: nuevoId });
    },
    eliminarPaciente(index) {
      this.listaPacientes.splice(index, 1);
    }
  }
};
</script>

<style>

body{
  background-color: #dfdfdf;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: #dfdfdf;
  
}

h1 {
  font-size: 2.5rem;
  font-weight: bold;
  font-family: Arial, Helvetica, sans-serif;
 
}
</style>
