<template>
    <div>
      <h1>Formulaire d'inscription</h1>
      <form @submit.prevent="submitForm">
        <div class="form-group">
          <label for="name">Nom :</label>
          <input type="text" id="name" v-model="name">
          <span v-if="errors.name" class="error">{{ errors.name }}</span>
        </div>
        
        <div class="form-group">
          <label for="email">Email :</label>
          <input type="email" id="email" v-model="email">
          <span v-if="errors.email" class="error">{{ errors.email }}</span>
        </div>
  
        <div class="form-group">
          <label for="phone">Téléphone :</label>
          <input type="tel" id="phone" v-model="phone">
          <span v-if="errors.phone" class="error">{{ errors.phone }}</span>
        </div>
  
        <button type="submit">Soumettre</button>
      </form>
      <p v-if="message" class="message">{{ message }}</p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: '',
        email: '',
        phone: '',
        errors: {},
        message: ''
      };
    },
    methods: {
      submitForm() {
        this.errors = {};
        if (!this.name) {
          this.errors.name = 'Le nom est requis.';
        }
        if (!this.email) {
          this.errors.email = 'L\'email est requis.';
        } else if (!this.validEmail(this.email)) {
          this.errors.email = 'L\'email n\'est pas valide.';
        }
        if (!this.phone) {
          this.errors.phone = 'Le téléphone est requis.';
        } else if (!this.validPhone(this.phone)) {
          this.errors.phone = 'Le numéro de téléphone n\'est pas valide.';
        }
  
        if (Object.keys(this.errors).length === 0) {
          this.message = 'Formulaire soumis avec succès !';
          this.clearForm();
        }
      },
      validEmail(email) {
        const re = /\S+@\S+\.\S+/;
        return re.test(email);
      },
      validPhone(phone) {
        const re = /^\d{10}$/;
        return re.test(phone);
      },
      clearForm() {
        this.name = '';
        this.email = '';
        this.phone = '';
      }
    }
  };
  </script>
  
  <style scoped>
  .form-group {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
  }
  
  input {
    width: 100%;
    padding: 8px;
    box-sizing: border-box;
  }
  
  button {
    padding: 10px 15px;
    background-color: #28a745;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .error {
    color: red;
    font-size: 12px;
    margin-top: 5px;
    display: block;
  }
  
  .message {
    margin-top: 20px;
    color: green;
  }
  </style>
  