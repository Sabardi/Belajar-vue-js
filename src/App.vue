<template>
  <form action="">
    <input type="text" placeholder="First name" v-model="firstname"> <br>
    <input type="text" placeholder="Middle name" v-model="midlename"> <br>
    <input type="text" placeholder="Last name" v-model="lastname"> <br>
  </form>

  <div>
    Full name: {{ fullname }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstname: '',
      midlename: '',
      lastname: '',
    }
  },
  computed: {
    // Computed property untuk full name
    fullname() {
      // Menggabungkan nama lengkap dari 3 input
      return `${this.firstname} ${this.midlename} ${this.lastname}`.trim();
    }
  }
}
</script>
