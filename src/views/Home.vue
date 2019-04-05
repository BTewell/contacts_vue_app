<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <hr>
    <div v-for="contact in contacts">
      <p>{{ contact.last_name }}{{", "}}{{ contact.first_name }}</p>
    </div>
  </div>
</template>

<style>
  img {
    width: 200px;
  }
</style>

<script>
import axios from 'axios';

export default {
  data: function() {
    return {
      message: "Welcome to your Contacts Application!",
      contacts: [],
    };
  },
  created: function() {
    axios.get("/api/contacts").then(response => {
      this.contacts = response.data;
    });
  },
  methods: {}
};
</script>