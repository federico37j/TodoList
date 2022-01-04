<template>
  <div id="search-container">
    <h3>Search</h3>
    <input
      type="text"
      v-model="query"
      v-on:input="$emit('query-change', query)"
    />
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      query: "",
    };
  },
};
</script>

<style scoped>
#search-container {
  width: 50%;
  margin: 0 auto;
  display: flex;
  padding: 2em;
  flex-direction: column;
}

@import url("https://fonts.googleapis.com/css2?family=Licorice&display=swap");
h3 {
  font-family: "Licorice", cursive;
  font-size: 2.3em;
}
input {
  padding: 10px;
  width: 100%;
  margin: 1em auto;
  margin-top: 0.5em;
}
</style>
