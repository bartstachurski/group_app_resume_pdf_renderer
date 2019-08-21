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
      message: "",
      skils: {},
      students: {},
      capstones: {},
      experiences: {},
      educations: {}
    };
  },
  created: function() {
    axios.get(`/students/${this.$route.params.id}`).then(response => { 
      this.students = response.data.student;
      console.log(response.data);
    });
    axios.get(`/educations/${this.$route.params.id}`).then(response => {
      this.educations = response.data.education;
      console.log(response.data);
    });
    axios.get(`/experiences/${this.$route.params.id}`).then(response => {
      this.experiences = response.data.experiences;
      console.log(response.data);
    });
    axios.get(`/capstones/${this.$route.params.id}`).then(response => {
      this.capstones = response.data.capstone;
      console.log(response.data);
    });
  },
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
      doc.text(this.photo, 10, 90);
      doc.text(this.name, 10, 90);
      doc.text(this.start_data, 10, 90);
      doc.text(this.end_date, 10, 90);
      doc.text(this.job_title, 10, 90);
      doc.text(this.company_name, 10, 90);
      doc.text(this.details, 10, 90);
      doc.text(this.student_id, 10, 90);
      doc.text(this.description, 10, 90);
      doc.text(this.url, 10, 90);
      doc.text(this.screenshot, 10, 90);
      doc.save(pdfName + '.pdf');
    }
  }
};
</script>