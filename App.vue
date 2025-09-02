<template>
  <div class="container">
    <h1>Gerador de QR Code</h1>
    <p>Digite um link para gerar o QR Code:</p>
    <input type="text" v-model="link" placeholder="Ex: https://www.google.com">
    <button @click="generateQRCode">Gerar QR Code</button>

    <div class="qrcode-wrapper">
      <canvas id="qrcode-canvas" v-if="link"></canvas>
    </div>
  </div>
</template>

<script>
import Qrious from 'qrious';

export default {
  data() {
    return {
      link: ''
    }
  },
  methods: {
    generateQRCode() {
      if (this.link) {
        // Cria uma nova instância do QR Code
        const qr = new Qrious({
          element: document.getElementById('qrcode-canvas'),
          value: this.link,
          size: 128
        });
      }
    }
  }
}
</script>

<style>
/* CSS global (aplica-se a todo o site) */
body {
    font-family: Arial, sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
    background-color: #f4f4f9;
}
</style>

<style scoped>
/* CSS local (aplica-se apenas a este componente) */
.container {
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    text-align: center;
}
.qrcode-wrapper {
    display: flex;
    justify-content: center;
    margin-top: 20px;
}
input {
  width: 80%;
  padding: 10px;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 4px;
}
button {
  padding: 10px 20px;
  border: none;
  background-color: #007BFF;
  color: white;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
}
button:hover {
  background-color: #0056b3;
}
</style>