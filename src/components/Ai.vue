<template>
    <!-- 1. Menggunakan v-on untuk Event Handling -->
    <button v-on:click="sayHello">Click me!</button>
  
    <!-- 2. Passing Data ke Method -->
    <button @click="sayMessage('Hello from Vue!')">Click me</button>
  
    <!-- 3. Menggunakan Event Modifier -->
    <form @submit.prevent="handleSubmit">
      <input type="text" v-model="inputValue" />
      <button type="submit">Submit</button>
    </form>
  
    <!-- 4. Methods dalam Vue.js -->
    <div>
      <p>{{ message }}</p>
      <button @click="changeMessage">Change Message</button>
    </div>
  </template>
  
  <script>
  export default {
    methods: {
      sayHello() {
        alert('Hello Vue.js!');
      },
      sayMessage(message) {
        alert(message);
      },
      handleSubmit() {
        alert('Form submitted with: ' + this.inputValue);
      },
      changeMessage() {
        this.message = 'Message has been changed!';
      }
    }
  }
  </script>
  