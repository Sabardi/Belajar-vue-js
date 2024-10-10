<template>
  <!-- 1. Binding ke Input Teks -->
  <div>
    <input v-model="message" placeholder="Ketik sesuatu">
    <p>Pesan: {{ message }}</p>
  </div>
  <!-- 2. Binding ke Checkbox -->
  <br>
  <div>
    <input type="checkbox" v-model="checked">
    <p>Checkbox tercentang: {{ checked }}</p>
  </div>
  <!-- 3. Binding ke Radio Button -->
  <br>
  <div>
    <label for="">Jenis kelamin</label>
    <br>
    <input type="radio" value="laki" v-model="picked"> Laki Laki
    <input type="radio" value="wanita" v-model="picked"> perempuan
    <p>Pilihan: {{ picked }}</p>
  </div>
  <br><br>
  <!-- 4. Binding ke Dropdown (Select) -->

  <div>
    <select v-model="selected">
      <option disabled value="">Pilih salah satu</option>
      <option value="A">Option A</option>
      <option value="B">Option B</option>
      <option value="C">Option C</option>
    </select>
    <p>Pilihan: {{ selected }}</p>
  </div>

  <!-- 5. Two-Way Binding pada Input dengan Modifier -->
  <br>
  <input v-model.lazy="message" placeholder="Tulis setelah blur">
  <br>
  <input v-model.number="age" type="number">
  <br>
  <input v-model.trim="name" placeholder="Tanpa spasi di ujung">

</template>

<script>
export default {
  data() {
    return {
      message: "",
      checked: false,
      picked: '',
      selected: ''
    }
  }
}
</script>
