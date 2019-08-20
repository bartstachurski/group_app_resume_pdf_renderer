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
      doc.text(this.first_name + " " + this.last_name, 10, 10);
      doc.text(this.email, 10, 20);
      doc.text(this.phone_number, 10, 30);
      doc.text(this.github_url, 10, 40);
      doc.text(this.twitter, 10, 50);
      doc.text(this.personal_url, 10, 60);
      doc.text(this.resume_url, 10, 70);
      doc.text(this.linkedin, 10, 80);
      doc.text(this.bio, 10, 90);
      doc.save(pdfName + '.pdf');
    }
  }
};
</script>