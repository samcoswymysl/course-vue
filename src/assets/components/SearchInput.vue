<template>
    <div class="searchWrapper">
      <input
        type="text"
        name="search"
        v-model="searchValue"
        @input="handleInput">

      <ul>
        <li v-for="(result, index) in results" :key="index">
          <p>{{ result.data[0].description}}</p>

        </li>
      </ul>
    </div>
</template>

<script>
export default {
  name: 'SearchInput',
};
</script>

<style lang="scss" scoped>

.searchWrapper {
  display: flex;
  flex-direction: column;
  width: 250px;
  margin: 60px 0 0 0 ;
}

input {
  height: 30px;
  border: 0;
  border-bottom: 1px solid black;
  background: none;
}

</style>
