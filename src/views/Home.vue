<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <button v-on:click="createPDF()">
    Create PDF</button>
  </div>
</template>

<style>
</style>

<script>
import jsPDF from 'jspdf';
import axios from 'axios';


export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!"
    };
  },
  created: function() {},
  methods: {
    createPDF() {
      axios.get();
      let pdfName = 'test'; 
      var doc = new jsPDF();
      doc.text("Hello Team", 10, 10);
      doc.save(pdfName + '.pdf');
    }
  }
};
</script>