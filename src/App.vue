<template>
  <div>
    <!-- Contoh penggunaan v-if, v-else-if, dan v-else -->
    <div v-if="role === 'admin'">
      <h2>Selamat datang Admin!</h2>
    </div>
    <div v-else-if="role === 'user'">
      <h2>Selamat datang Pengguna!</h2>
    </div>
    <div v-else>
      <h2>Silakan login atau daftar untuk melanjutkan</h2>
    </div>

    <!-- Contoh penggunaan v-show -->
    <button @click="toggleVisibility">
      {{ isVisible ? 'Sembunyikan' : 'Tampilkan' }} Pesan
    </button>
    <div v-show="isVisible">
      <p>Ini adalah pesan yang bisa disembunyikan atau ditampilkan.</p>
    </div>
  </div>

  <br>
  <div class="" v-show="kondisilampu">Lampu hidup</div>
  <button @click="togleLampu">matikan</button>
</template>

<script>
export default {
  data() {
    return {
      role: 'guest', 
      isVisible: true, 
      kondisilampu: false
    };
  },
  methods: {
    toggleVisibility() {
      this.isVisible = !this.isVisible;
    },
    togleLampu() {
      this.kondisilampu = !this.kondisilampu
    }
  }
};
</script>
