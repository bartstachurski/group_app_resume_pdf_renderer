<template>
   <div class="home">
       
       <button v-on:click="createPDF()">Create PDF</button>
   </div>
</template>

<style>
</style>

<script>
import jsPDF from 'jspdf';


export default {
  data: function() {
    return {
      message: "",
      first_name: "Arzo",
      last_name: "Thakur",
      email: "arzo@actualize.com",
      phone_number: "7089453333",
      bio: "text",
      linkedin: "/softwareneginerr",
      twitter: "www.arzo.com",
      personal_url: "not yet",
      resume_url: "indeed resume",
      github_url: "nonsense"
    
    };
  },
  created: function() {},
  methods: {
    createPDF() {
      let pdfName = 'test'; 
      var doc = new jsPDF();
      doc.text(this.first_name, 10, 10);
      doc.save(pdfName + '.pdf');
    }
  }
};
</script>