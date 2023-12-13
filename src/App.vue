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

const addContact = () => {
  // Add new contact to the contacts array
  contacts.value.push({
    name: newName.value,
    number: newNumber.value,
    Address: newAddress.value,
  });

  // Clear the form fields
  newName.value = "";
  newNumber.value = "";
  newAddress.value = "";
};

const newName = ref("");
const newNumber = ref("");
const newAddress = ref("");


const filteredContacts = ref([]);

const searchContacts = () => {
  const searchTerm = searchInput.value.toLowerCase();
  filteredContacts.value = contacts.value.filter(contact =>
    contact.name.toLowerCase().includes(searchTerm)
  );
};

</script>
<template>
  <div class="app-container">
    <div class="title">
      <h2>Contact List</h2>
    </div>

    <div class="search-container">
      <label for="searchInput">Search by Name:</label>
      <input
        v-model="searchInput"
        type="text"
        id="searchInput"
        @input="searchContacts"
        placeholder="Search..."
      />
    </div>

    <div class="contact-container">
      <div v-if="searchInput && filteredContacts.length > 0">
        <div v-for="(contact, index) in filteredContacts" :key="index" class="contact-card">
          <div class="contact-info">
            <p><strong>Name:</strong> {{ contact.name }}</p>
            <p><strong>Number:</strong> {{ contact.number }}</p>
            <p><strong>Address:</strong> {{ contact.Address }}</p>
          </div>
          <hr />
        </div>
      </div>
      <div v-else-if="searchInput && filteredContacts.length === 0" class="not-found">
        <p>No contacts found.</p>
      </div>
    </div>

    <div v-if="!searchInput" class="contact-form-container">
      <form class="contact-form" @submit.prevent="addContact">
        <label for="newName">Name:</label>
        <input v-model="newName" type="text" id="newName" required />

        <label for="newNumber">Number:</label>
        <input v-model="newNumber" type="text" id="newNumber" required />

        <label for="newAddress">Address:</label>
        <input v-model="newAddress" type="text" id="newAddress" required />

        <button type="submit">Add Contact</button>
      </form>
    </div>
  </div>

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
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f5f5f5;
  margin: 0;
}

.app-container {
  max-width: 800px;
  margin: 50px auto;
  padding: 20px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
}

.title {
  text-align: center;
  margin-bottom: 20px;
}

.search-container {
  text-align: center;
  margin-bottom: 20px;
}

.contact-container {
  display: flex;
  flex-wrap: wrap;
  justify-content:space-evenly; 
  max-width: 1024px;
  margin: 50px auto;
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

.not-found {
  text-align: center;
  color: #777;
}

.contact-form-container {
  text-align: center;
  margin-top: 20px;
}

.contact-form {
  max-width: 400px;
  margin: 0 auto;
}

.contact-form label {
  display: block;
  margin-bottom: 8px;
  font-weight: bold;
}

.contact-form input {
  width: 100%;
  padding: 10px;
  margin-bottom: 16px;
  border: 1px solid #ddd;
  border-radius: 4px;
  box-sizing: border-box;
}

.contact-form button {
  background-color: #4caf50;
  color: #fff;
  padding: 10px 15px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
}

.contact-form button:hover {
  background-color: #45a049;
}
</style>
