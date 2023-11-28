<script setup>
import { ref } from "vue";


const searchInput = ref("");
let contacts = ref([
  {
    name: "Leonel angelo",
    number: "09123456789",
    Address: "San vicente, Bulan",
  },
  {
    name: "Britney Hubilla",
    number: "09123456780",
    Address: "San francisco, Bulan",
  },
  {
    name: "Wendy Mahusay",
    number: "09123456712",
    Address: "Zone 2, Bulan",
  },
  {
    name: "Diana De Guzman",
    number: "09123456232",
    Address: "Zone 4, Bulan",
  },
  {
    name: "Jeniffer Borres",
    number: "09123456234",
    Address: "Basta, Juban",
  },
]);



</script>
<template>

<div class="title">
  <h2>List of Contacts</h2>
</div>

<div class="contact-container">
    <div v-for="(contacts) in contacts" class="contact-card">
      <p><strong>Name:</strong> {{ contacts.name }}</p>
      <p><strong>Number:</strong> {{ contacts.number }}</p>
      <p><strong>Address:</strong> {{ contacts.Address }}</p> 
      <hr />
    </div>
  </div>
  
</template>


<style>
body {
  display: flex;
  justify-content: center;
}

.main-container{
  margin-top: 50px;
  display: flex;
  justify-content: center;
  font-weight: bold;
}

.title{
  display: flex;
  justify-content: center;
  margin-top: 80px;
  margin-bottom: 25px;
}

.contact-container {
  display: flex;
  flex-wrap: wrap;
  justify-content:space-evenly; 
  max-width: 1024px;
}

.contact-card {
  margin-top: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 16px;
  width: 300px;
  margin-bottom: 16px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: #fff;
}

.contact-card p {
  margin: 8px 0;
}

.contact-card hr {
  border: none;
  border-top: 1px solid #ccc;
  margin: 10px 0;
}
</style>