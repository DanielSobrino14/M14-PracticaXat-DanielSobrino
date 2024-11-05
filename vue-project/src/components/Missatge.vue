<template>
    <div class="contenedor-mensaje">
      <input v-model="mensaje" type="text" placeholder="Escribe un mensaje..." />
      <button @click="enviarMensaje">Enviar</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import { defineEmits, defineProps } from 'vue';
  
  const props = defineProps({
    autor: String,
  });
  
  const emit = defineEmits();
  const mensaje = ref('');
  
  function enviarMensaje() {
    if (mensaje.value.trim() !== '') {
      emit('enviar-mensaje', { autor: props.autor, texto: mensaje.value });
      mensaje.value = '';
    }
  }
  </script>
  
  <style scoped>
  .contenedor-mensaje {
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
  }
  
  input {
    width: 75%;
    padding: 10px;
    margin-right: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 16px;
    transition: all 0.3s ease;
  }
  
  input:focus {
    border-color: #007bff;
    box-shadow: 0 0 8px rgba(0, 123, 255, 0.2);
  }
  
  button {
    padding: 10px 20px;
    border: none;
    background-color: #0044ff;
    color: white;
    border-radius: 5px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
  }
  
  button:hover {
    background-color: #07a2c9;
    transform: translateY(-2px);
  }
  
  button:active {
    background-color: #1e7e34;
    transform: translateY(0);
  }
  </style>