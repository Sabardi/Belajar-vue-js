### **Watchers di Vue.js | Mengatasi Reactive Error Message pada Form**

**Watchers** di Vue.js memungkinkan kita untuk **memantau perubahan** pada data tertentu dan mengeksekusi fungsi atau logika ketika nilai data tersebut berubah. Watchers sering digunakan untuk menangani **validasi atau error handling** di form, misalnya menampilkan pesan kesalahan jika pengguna memasukkan data yang tidak valid.

#### Kasus Penggunaan:
Misalnya, kita ingin memantau input pada form dan memberikan **error message** secara reaktif, seperti jika `firstname`, `midlename`, atau `lastname` tidak diisi atau memiliki kesalahan tertentu. Ketika nilai input berubah, watcher akan memberikan feedback kepada pengguna secara otomatis.

---

### **Contoh Implementasi: Watchers untuk Reactive Error Message pada Form**

```vue
<template>
  <form action="">
    <input 
      type="text" 
      placeholder="First name" 
      v-model="firstname"
    > <br>
    <span v-if="errors.firstname" class="error">{{ errors.firstname }}</span> <br>

    <input 
      type="text" 
      placeholder="Middle name" 
      v-model="midlename"
    > <br>
    <span v-if="errors.midlename" class="error">{{ errors.midlename }}</span> <br>

    <input 
      type="text" 
      placeholder="Last name" 
      v-model="lastname"
    > <br>
    <span v-if="errors.lastname" class="error">{{ errors.lastname }}</span> <br>

    <div>
      Full name: {{ fullname }}
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      firstname: '',
      midlename: '',
      lastname: '',
      errors: {
        firstname: '',
        midlename: '',
        lastname: ''
      }
    }
  },
  computed: {
    // Computed property untuk full name
    fullname() {
      return `${this.firstname} ${this.midlename} ${this.lastname}`.trim();
    }
  },
  watch: {
    // Watch untuk firstname
    firstname(newValue) {
      if (!newValue) {
        this.errors.firstname = 'First name is required';
      } else {
        this.errors.firstname = '';
      }
    },
    // Watch untuk midlename
    midlename(newValue) {
      if (!newValue) {
        this.errors.midlename = 'Middle name is required';
      } else {
        this.errors.midlename = '';
      }
    },
    // Watch untuk lastname
    lastname(newValue) {
      if (!newValue) {
        this.errors.lastname = 'Last name is required';
      } else {
        this.errors.lastname = '';
      }
    }
  }
}
</script>

<style>
.error {
  color: red;
  font-size: 12px;
}
</style>
```

### **Penjelasan:**

1. **`v-model`**: Digunakan untuk **two-way data binding** pada input form. Setiap kali pengguna mengetik, data akan diupdate di `firstname`, `midlename`, dan `lastname`.
  
2. **`errors` Object**: Properti `errors` digunakan untuk menyimpan pesan kesalahan validasi untuk setiap field.

3. **`watch`**: Menggunakan **watchers** untuk memantau perubahan pada `firstname`, `midlename`, dan `lastname`. Setiap kali ada perubahan pada input:
   - Jika nilai input kosong, maka akan diset error message terkait, misalnya, "First name is required".
   - Jika ada nilai (tidak kosong), error message akan dikosongkan.

4. **Error Message**: Error message untuk setiap input hanya akan ditampilkan jika ada kesalahan pada input yang bersangkutan. Ini dikendalikan dengan `v-if` dan objek `errors`.

5. **Style Error**: Untuk memberi tanda visual, error message diberi styling dengan class `error`, yang membuat teks menjadi merah dan ukuran font lebih kecil.

---

### **Best Practices untuk Watchers dan Form Validation**

1. **Validasi Input Sederhana**:
   - Gunakan watcher untuk validasi input yang mudah, seperti memastikan input tidak kosong, atau format tertentu (misalnya, email).
   
2. **Menggunakan Vue Validator**:
   - Untuk form validasi yang lebih kompleks, pertimbangkan menggunakan library seperti **VeeValidate** atau **Vuelidate** yang sudah menyediakan validasi yang lebih terstruktur dan lengkap.

3. **Bersihkan Validasi Saat Input Diperbaiki**:
   - Pastikan pesan error hilang segera setelah input yang valid dimasukkan, seperti yang dilakukan di atas dengan mengosongkan pesan kesalahan saat input valid.

4. **Hindari Penggunaan Watch untuk Semua Kasus**:
   - Gunakan **computed properties** jika logika perhitungan lebih sederhana dan tidak memerlukan pemantauan secara langsung.

5. **Terapkan `debounce` untuk Mengurangi Overhead**:
   - Jika validasi input dilakukan dalam bentuk pemanggilan API atau proses yang memakan waktu, pertimbangkan untuk menggunakan **debouncing** untuk mengurangi frekuensi validasi.

Dengan menggunakan watchers, kita dapat memberikan **reaktif feedback** kepada pengguna ketika mereka mengisi form, membantu mereka untuk memperbaiki kesalahan input secara langsung dan meningkatkan pengalaman pengguna aplikasi Vue.js kita.