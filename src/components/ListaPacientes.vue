<template>
  <div id="lista-pacientes">
    <div v-if="listaPacientes.length > 0" class="cardPacienteContainer">
      <div v-for="(paciente, index) in listaPacientes" :key="paciente.id" class="cardPaciente">
        <div :class="getClassByGravedad(paciente.gravedad)">
          <h4>Nombre</h4>
          <p>{{ paciente.nombre }}</p>
          <h4>Fecha</h4>
          <p>{{ paciente.fecha }}</p>
          <h4>Hora</h4>
          <p>{{ paciente.hora }}</p>
          <h4>Gravedad</h4>
          <p>{{ paciente.gravedad }}</p>
          <h4>Motivo</h4>
          <p>{{ paciente.motivo }}</p>
          <button @click="eliminarPaciente(index)">Eliminar</button>
        </div>
      </div>
    </div>
    <div v-else>
      <p>No hay pacientes en la lista.</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    listaPacientes: {
      type: Array,
      required: true
    }
  },
  methods: {
    eliminarPaciente(index) {
      this.$emit('eliminar-paciente', index);
    },
    getClassByGravedad(gravedad) {
      switch (gravedad.toLowerCase()) {
        case 'alta':
          return 'rojo';
        case 'media':
          return 'amarillo';
        case 'baja':
          return 'verde';
        default:
          return '';
      }
    }
  }
};
</script>

<style>
#lista-pacientes {
  margin-top: 20px;
  display: flex;
  justify-content: center;
}

.cardPacienteContainer {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.cardPaciente {
  width: 250px;
  margin: 10px;
  border-radius: 1rem;
  /* border: 1px solid #2B3D4F; */

}

.cardPaciente h4 {
  margin: 0;
  padding: 0.5rem;
  font-size: 1rem;
  font-weight: bold;
  color: #37373d;
}

.cardPaciente p {
  margin: 0.25rem 0 0.5rem 0;
  color: #555;
}

.cardPaciente button {
  margin: 1rem;
  padding: 0.5rem 1rem;
  color: #f31010;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
  background-color: #a19797;
}

.cardPaciente button:hover {
  background-color: #e93a3a;
  color:white;
  font-weight: bold;
}

.verde {
  background-color: white;
  border: rgba(30, 255, 0, 0.473) solid 3px;
  border-radius: 0.5rem; 

}

.amarillo {
  background-color: white;
  border: rgba(238, 255, 0, 0.473) solid 3px;
  /* background-color: rgba(255, 255, 0, 0.493); */
  border-radius: 0.5rem; 
 
}

.rojo {
  background-color: white;
  border: rgba(255, 0, 0, 0.473) solid 3px;
  border-radius: 0.5rem; 
 
}

</style>
