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
      skills: "",
      students: "",
      capstones: "",
      experiences: "",
      educations: "",
      first_name: "",
      last_name: "",
      email: "",
      phone_number: "",
      bio: "",
      linkedin: "",
      twitter: "",
      personal_url: "",
      resume_url: "",
      github_url: "",
      photo: "",
      exp_start_data: "",
      exp_end_date: "",
      job_title: "",
      company_name:"",
      exp_details: "", 
      start_data: "",
      end_date: "",
      degree: "",
      university: "",
      edu_details: "",
      cap_name: "",
      description: "",
      url: "",
      screenshot: ""


    };
  },
  created: function() {
    axios.get(`api/students/${this.$route.params.id}`).then(response => { 
      this.first_name = response.data.first_name;
    console.log(response.data);
  
    this.last_name = response.data.last_name;
      console.log(response.data);
  
    this.email = response.data.email;
      console.log(response.data);
  
    this.phone_number = response.data.phone_number;
      console.log(response.data);
    
    this.bio = response.data.bio;
      console.log(response.data);
    
    this.linkedin = response.data.linkedin;
      console.log(response.data);
  
    this.twitter = response.data.twitter;
      console.log(response.data);
    
    this.personal_url = response.data.personal_url;
      console.log(response.data);
    
    this.resume_url = response.data.resume_url;
      console.log(response.data);
  
    this.github_url = response.data.github_url;
      console.log(response.data);
    
    this.photo = response.data.photo;
     
    });
    axios.get(`api/educations/${this.$route.params.id}`).then(response => {
      this.educations = response.data.university;
      console.log(response.data);
    });
    axios.get(`api/experiences/${this.$route.params.id}`).then(response => {
      this.experiences = response.data.company_name;
      console.log(response.data);
    });
    axios.get(`api/capstones/${this.$route.params.id}`).then(response => {
      this.capstones = response.data.url;
      console.log(response.data);
    });  
    axios.get(`api/skills/${this.$route.params.id}`).then(response => {
      this.skills = response.data.name;
      console.log(response.data);
    });
  },
  methods: {
    createPDF() { 
      let pdfName = 'test'; 
      var doc = new jsPDF();
      // doc.text(this.capstones, 10, 10);
      // doc.text(this.skills, 10, 20);
      // doc.text(this.educations, 10, 30);
      // doc.text(this.experiences, 10, 40);
      doc.text(this.students, 10, 10);
      doc.text(this.educations, 10, 20);
      doc.text(this.experiences, 10, 30);
      doc.text(this.capstones, 10, 40);
      doc.text(this.skills, 10, 50);
      doc.text(this.personal_url, 10, 60);
      doc.text(this.resume_url, 10, 70);
      doc.text(this.first_name, 10, 80);
      doc.text(this.last_name, 10, 90);
      doc.text(this.email, 10, 100);
      doc.text(this.phone_number, 10, 110);
      doc.text(this.bio, 10, 120);
      doc.text(this.linkedin, 10, 130);
      doc.text(this.twitter, 10, 140);
      doc.text(this.github_url, 10, 150);
      doc.text(this.photo, 10, 160);
      // doc.text(this.photo, 10, 90);
      // doc.text(this.name, 10, 90);
      // doc.text(this.start_data, 10, 90);
      // doc.text(this.end_date, 10, 90);
      // doc.text(this.job_title, 10, 90);
      // doc.text(this.company_name, 10, 90);
      // doc.text(this.details, 10, 90);
      // doc.text(this.student_id, 10, 90);
      // doc.text(this.description, 10, 90);
      // doc.text(this.url, 10, 90);
      // doc.text(this.screenshot, 10, 90);
      doc.save(pdfName + '.pdf');
    }
  }
};
</script>