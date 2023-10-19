<template>
  <body>
    <h1>Cifrado y Descifrado Simétrico RC4</h1>

    <div class="container">
      <h3>Ingresa aquí el mensaje a encriptar o desencriptar</h3>
      <textarea v-model="plaintext" placeholder="Texto a cifrar/descifrar"></textarea>
      <div class="botones">
        <button @click="encrypt">Cifrar</button>
        <button @click="decrypt">Descifrar</button>
      </div>
      <div id="resultado">
        <h3>Resultado:</h3>
        <p>{{ resultado }}</p>
      </div>
    </div>
  </body>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import * as CryptoJS from 'crypto-js';

</script>

<script lang="ts">
const plaintext = ref<string>('');
const key = 'angel'; // Cambia esto con tu clave secreta
const resultado = ref<string>('');
const encrypt = () => {
  resultado.value = CryptoJS.RC4.encrypt(plaintext.value, key).toString();
};

const decrypt = () => {
  resultado.value = CryptoJS.RC4.decrypt(resultado.value, key).toString(CryptoJS.enc.Utf8);
};
</script>

<style scoped>
body {
  font-family: monospace;
  background-color: #176B87;
  margin: 0;
  padding: 0;
}

.botones{
  text-align: center;
}

h3 {
  text-align: center;
  font-family: monospace;
  font-size: 20px;
  color: #333;
  margin-bottom: 10px;
  font-weight: 700;
}

h1 {
  text-align: center;
  background-color: #04364A;
  color: #fff;
  padding: 20px;
  margin: 0;
}

.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: #DAFFFB;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  margin-top: 30px;
}

textarea,
input {
  font-family: monospace;
  font-size: 16px;
  width: 100%;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 3px;
}

button {
  font-family: monospace;
  background-color: #04364A;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  margin: 0 20px;
  font-weight: bold;
  font-size: 14px;
  margin-bottom: 30px;
}

button:hover {
  background-color: #64CCC5;
}

p {
  height: 100px;
  margin-top: 20px;
  color: #04364A;
  text-align: center;
  font-weight: bold;
}
</style>
