<template>
  <div class="underline text-2xl uppercase">welcome home</div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      datas: [],
    };
  },
  methods: {
    getData() {
      axios.get("https://jsonplaceholder.typicode.com/posts").then((res) => {
        console.log(res.data);
      });
    },
  },

};
</script>

<style></style>
