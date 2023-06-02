<template>
    <div>
      <h1>NASA Obrazki</h1>
      <div v-for="item in items" :key="item.data[0].nasa_id">
        <h2>{{ item.data[0].title }}</h2>
        <p>{{ item.data[0].description }}</p>
        <img :src="item.links[0].href" :alt="item.data[0].title" width="200px" height="200px"/>
        <hr />
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        items: []
      };
    },
    async created() {
      const response = await fetch('https://images-api.nasa.gov/search?q=sun');
      const data = await response.json();
      this.items = data.collection.items;
    }
  };
  </script>