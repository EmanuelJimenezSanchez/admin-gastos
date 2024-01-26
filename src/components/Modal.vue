<script setup>
  import cerrarModal from "../assets/img/cerrar.svg"

  const emit = defineEmits(["ocultar-modal"])

  const props = defineProps({
    modal: {
      type: Object,
      required: true
    }
  })
</script>

<template>
  <div class="modal">
    <div class="cerrar-modal">
      <img
        :src="cerrarModal"
        alt="Cerrar Modal"
        @click="emit('ocultar-modal')"
      />
    </div>

    <div 
      class="contenedor contenedor-formulario"
      :class="[modal.animar ? 'animar' : 'cerrar']"
    >
      <form class="nuevo-gasto">
        <legend>Añadir Gasto</legend>

        <div class="campo">
          <label for="nombre">Nombre Gasto:</label>
          <input 
            type="text" 
            id="nombre" 
            placeholder="Ej. Transporte" 
          />
        </div>

        <div class="campo">
          <label for="cantidad">cantidad:</label>
          <input 
            type="number" 
            id="cantidad" 
            placeholder="Ej. 300" 
          />
        </div>

        <div class="campo">
          <label for="categoria">Categoria:</label>
          <select id="categoria">
            <option value="" selected disabled>-- Seleccione --</option>
            <option value="ahorro">Ahorro</option>
            <option value="comida">Comida</option>
            <option value="casa">Casa</option>
            <option value="gastos">Gastos Varios</option>
            <option value="ocio">Ocio</option>
            <option value="salud">Salud</option>
            <option value="suscripciones">Suscripciones</option>
          </select>
        </div>

        <input type="submit" value="Añadir Gasto">
      </form>
    </div>
  </div>
</template>



<style scoped>
  .modal {
    position: absolute;
    background-color: rgb(0 0 0 / 0.9);
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
  }

  .cerrar-modal {
    position: absolute;
    top: 3rem;
    right: 3rem;
  }

  .cerrar-modal img {
    width: 3rem;
    cursor: pointer;
  }

  .contenedor-formulario {
    transition-property: all;
    transition-duration: 300ms;
    transition-timing-function: ease-in;
    opacity: 0;
  }

  .contenedor-formulario.animar {
    opacity: 1;
  }

  .contenedor-formulario.cerrar {
    opacity: 0;
  }

  .nuevo-gasto {
    margin: 10rem auto 0 auto;
    display: grid;
    gap: 2rem;
  }

  .nuevo-gasto legend {
    text-align: center;
    color: var(--blanco);
    font-size: 3rem;
    font-weight: 700;
  }

  .campo {
    display: grid;
    gap: 2rem;
  }

  .nuevo-gasto input,
  .nuevo-gasto select {
    background-color: var(--gris-claro);
    padding: 1rem;
    border-radius: 1rem;
    border: none;
    font-size: 2.2rem;
  }

  .nuevo-gasto label {
    color: var(--blanco);
    font-size: 3rem;
  }

  .nuevo-gasto input[type="submit"] {
    background-color: var(--azul);
    color: var(--blanco);
    font-weight: 700;
    cursor: pointer;
  }
</style>  