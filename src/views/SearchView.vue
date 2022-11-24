<template>
  <div class="w-3/5 mx-auto">
    <div class="flex justify-center items-center mt-5 py-5 rounded-t p-2">
      <form class="flex items-center w-1/2" @submit.prevent="searchNumber()">
        <!-- button click search -->
        <label for="simple-search" class="sr-only">Search</label>
        <div class="inset-y-0 left-0 flex items-center">
          <span
            id="dropdown-button"
            class="flex-shrink-0 inline-flex items-center py-2.5 px-4 text-sm font-medium text-center text-gray-900 bg-gray-100 border border-gray-300 rounded-l-lg hover:bg-gray-200 focus:ring-4 focus:outline-none focus:ring-gray-100"
            type="button"
          >
            +855
          </span>
        </div>
        <div class="relative w-full">
          <input
            type="number"
            id="simple-search"
            class="bg-gray-50 border outline-none border-gray-300 text-gray-900 text-sm rounded-r focus:ring-blue-500 focus:border-blue-500 block w-full pl-10 p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
            placeholder="Search"
            v-model="number"
            required
            oninput="this.value = this.value.replace(/[^0-9.]/g, '').replace(/(\..*)\./g, '$1');"
            maxlength="9"
          />
        </div>
        <button
          type="submit"
          class="p-2.5 ml-2 outline-none text-sm font-medium text-white bg-blue-700 rounded-lg border"
        >
          <svg
            class="w-5 h-5"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"
            ></path>
          </svg>
          <span class="sr-only">Search</span>
        </button>
      </form>
    </div>
    <div class=" ">
      <div v-if="first_name != ''">
        <CardUser
          :first_name="first_name"
          :last_name="last_name"
          :is_user_verify="is_user_verify"
        />
      </div>
    </div>
    <div></div>
  </div>
</template>
<script>
import axios from "axios";
import CardUser from "../components/CardUser.vue";
export default {
  components: { CardUser },
  data() {
    return {
      number: null,
      filter_number: null,
      url: "https://api.staging.bidnowkh.com/api/v1",
      url_phone: "/enrollments/get_user_phone?phone=",
      country_code: "&country_code=855",
      first_name: "",
      last_name: "",
      is_user_verify: false,
    };
  },
  methods: {
    searchNumber() {
      this.filter_number = this.number;
      this.number = "";
      axios
        .get(this.url + this.url_phone + this.filter_number + this.country_code)
        .then((res) => {
          this.first_name = res.data.data.first_name;
          this.last_name = res.data.data.last_name;
          this.is_user_verify = res.data.data.is_user_verify;
        });
    },
  },
};
</script>

<style scoped>
.h {
  height: 70vh;
}
</style>
