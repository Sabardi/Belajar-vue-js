<template>
  <div>
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.name }}</li>
    </ul>
  </div>
  <div>
    <ul>
      <li v-for="(item, index) in items" :key="item.id">
        {{ index + 1 }}. {{ item.name }}
      </li>
    </ul>
  </div>

  <div>
    <ul>
      <li v-for="(value, key) in user" :key="key">
        {{ key }}: {{ value }}
      </li>
    </ul>
  </div>

  <br>
  <br>
  <h1>Tips penggunaan for</h1>


  <div>
    <ul v-for="(category, index) in categories" :key="index">
      <li>{{ category.name }}</li>
      <ul>
        <li v-for="(item, subIndex) in category.items" :key="subIndex">
          {{ item }} <button @click="hapus">Hapus</button>
        </li>
      </ul>
    </ul>

  </div>

</template>

<script>
export default {
  data() {
    return {
      items: [
        { id: 1, name: 'Item 1' },
        { id: 2, name: 'Item 2' },
        { id: 3, name: 'Item 3' }
      ],
      user: {
        name: 'John Doe',
        age: 30
      },
      categories: [
        { name: 'Fruits', items: ['Apple', 'Banana', 'Orange'] },
        { name: 'Vegetables', items: ['Carrot', 'Broccoli', 'Spinach'] }
      ],
    };
  }
};
</script>
