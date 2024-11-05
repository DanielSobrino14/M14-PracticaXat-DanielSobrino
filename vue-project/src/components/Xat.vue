<template>
    <div class="contenedor-chat">
      <h1>Chat</h1>
      <ul>
        <li v-for="(msg, index) in mensajes" :key="index">
          <strong>{{ msg.autor }}:</strong> {{ msg.texto }}
        </li>
      </ul>
      <Missatge @enviar-mensaje="agregarMensaje" :autor="autor" />
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import Missatge from './Missatge.vue';
  
  const mensajes = ref([]);
  const autor = "Usuario";
  
  function agregarMensaje(nuevoMensaje) {
    mensajes.value.push(nuevoMensaje);
  }
  </script>
  
  <style scoped>
  .contenedor-chat {
    width: 100%;
    max-width: 600px;
    margin: 0 auto;
    padding: 30px;
    border-radius: 10px;
    background: linear-gradient(145deg, #ffffff, #e6e6e6);
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    text-align: left;
  }
  
  h1 {
    text-align: center;
    color: #fc0606;
    margin-bottom: 20px;
    font-size: 24px;
    font-weight: 700;
  }
  li {
    padding: 10px;
    margin-bottom: 10px;
    background-color: #f4f4f4;
    border-radius: 5px;
    transition: background-color 0.3s ease;
  }
  
  li:hover {
    background-color: #e9ecef;
  }
  
  li strong {
    color: #05d8f8;
  }
  
  ul::-webkit-scrollbar {
    width: 8px;
  }
  
  ul::-webkit-scrollbar-thumb {
    background-color: #007bff;
    border-radius: 4px;
  }
  
  ul::-webkit-scrollbar-track {
    background-color: #e9e9e9;
  }
  </style>