<template>
  <div class="wrapper">
    <Claim />
    <SearchInput />

  </div>
</template>
git
<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/assets/components/Claim.vue';
import SearchInput from '@/assets/components/SearchInput.vue';

const API = 'https://images-api.nasa.gov/search?';

export default {
  name: 'Search',
  components: {
    Claim,
    SearchInput,
  },
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
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  margin: 0;
  padding: 30px;
  background-image: url('../assets/home.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 50% 0%;

}
</style>
