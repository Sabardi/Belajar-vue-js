<template>
  <div class="container mt-5">
    <h2>Register</h2>
    <form @submit.prevent="handleSubmit">
      <!-- Full Name -->
      <div class="mb-3">
        <label for="name" class="form-label">Full Name</label>
        <input 
          type="text" 
          id="name" 
          v-model="name" 
          class="form-control" 
          placeholder="Enter your full name"
          required
        />
        <div v-if="errors.name" class="text-danger">{{ errors.name }}</div>
      </div>

      <!-- Email -->
      <div class="mb-3">
        <label for="email" class="form-label">Email address</label>
        <input 
          type="email" 
          id="email" 
          v-model="email" 
          class="form-control" 
          placeholder="Enter your email"
          required
        />
        <div v-if="errors.email" class="text-danger">{{ errors.email }}</div>
      </div>

      <!-- Password -->
      <div class="mb-3">
        <label for="password" class="form-label">Password</label>
        <input 
          type="password" 
          id="password" 
          v-model="password" 
          class="form-control" 
          placeholder="Enter your password"
          required
        />
        <div v-if="errors.password" class="text-danger">{{ errors.password }}</div>
      </div>

      <!-- Confirm Password -->
      <div class="mb-3">
        <label for="confirmPassword" class="form-label">Confirm Password</label>
        <input 
          type="password" 
          id="confirmPassword" 
          v-model="confirmPassword" 
          class="form-control" 
          placeholder="Confirm your password"
          required
        />
        <div v-if="errors.confirmPassword" class="text-danger">{{ errors.confirmPassword }}</div>
      </div>

      <!-- Submit Button -->
      <button type="submit" class="btn btn-primary">Register</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      password: '',
      confirmPassword: '',
      errors: {
        name: '',
        email: '',
        password: '',
        confirmPassword: ''
      }
    };
  },
  methods: {
    // Function to validate form
    validateForm() {
      this.errors.name = this.name ? '' : 'Full name is required';
      this.errors.email = this.email ? '' : 'Email is required';
      this.errors.password = this.password ? '' : 'Password is required';
      this.errors.confirmPassword = 
        this.confirmPassword === this.password ? '' : 'Passwords do not match';
      
      // Return true if there are no errors
      return !Object.values(this.errors).some(error => error !== '');
    },
    // Handle form submission
    handleSubmit() {
      if (this.validateForm()) {
        alert('Form submitted successfully');
        // Implement actual form submission logic (e.g., API call) here
      } else {
        alert('Please fill out the form correctly');
      }
    }
  }
};
</script>

<style scoped>
/* Add any custom styles here */
.container {
  max-width: 600px;
}
.text-danger {
  font-size: 0.875em;
}
</style>
