<template>
  <div class="wrapper">
    <div class="search">
      <label htmlFor="search">Search</label>
      <input
        type="text"
        name="search"
        id="search"
        v-model="searchValue"
        @input="handleInput">

    <ul>
      <li v-for="(result, index) in results" :key="index">
        <p>{{ result.data[0].description}}</p>

      </li>
    </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/search?';

export default {
  name: 'Search',
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleInput: debounce(function () {
      axios.get(`${API}q=${this.searchValue}&media_type=image`)
        .then((res) => {
          this.results = res.data.collection.items;
          console.log(res.data.collection.items);
        })
        .catch((er) => {
          console.log(er);
        });
    }, 1000),
  },

};
</script>

<style lang="scss" scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  margin: 0;
  padding: 30px;
}

.search {
  display: flex;
  flex-direction: column;
  width: 300px;
}

label {
  font-family: Monospaced, sans-serif;
}

input {
  height: 30px;
  border: 0;
  border-bottom: 1px solid black;
}

</style>
