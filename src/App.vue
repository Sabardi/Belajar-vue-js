<template>
  <!-- <div>
    <button v-on:click="count--">-</button>
    <span v-if="count > 0">{{ count }}</span>
    <button v-on:click="count++">+</button>
  </div> -->

  <!-- atau bisa menggunakan @click -->
  <div>
    <button @click="count--">-</button>
    <span v-if="count >0">{{ count }}</span>
    <button @click="count++">+</button>
  </div>

</template>

<script>
export default {
  data() {
    return {
      count: 0,
    }
  }
}
</script>