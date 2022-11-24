<template>
  <div
    class="box-shadow rounded-t bg-gray-200 shadow-lg p-2 dark:text-gray-100 w-1/2 mx-auto break-words"
  >
    <div class="flex justify-between text-2sm text-gray-700">
      <div class="felx justify-between">
        <p><span class="text-normal">First Name: </span></p>
      </div>
      <div class="felx justify-between">
        <p>
          <span class="text-normal"> {{ first_name }} </span>
        </p>
      </div>
    </div>
    <div class="flex justify-between text-2sm text-gray-700">
      <div class="felx justify-between">
        <p><span class="text-normal">Last Name: </span></p>
      </div>
      <div class="felx justify-between">
        <p>
          <span class="text-normal"> {{ last_name }} </span>
        </p>
      </div>
    </div>
    <div class="flex justify-center">
      <div>
        <div
          v-if="is_user_verify == false"
          class="border text-red-700 px-3 py-1 rounded flex relative"
          role="alert"
        >
          <svg
            class="fill-current h-6 w-6 text-red-500"
            role="button"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 20 20"
          >
            <title>Close</title>
            <path
              d="M14.348 14.849a1.2 1.2 0 0 1-1.697 0L10 11.819l-2.651 3.029a1.2 1.2 0 1 1-1.697-1.697l2.758-3.15-2.759-3.152a1.2 1.2 0 1 1 1.697-1.697L10 8.183l2.651-3.031a1.2 1.2 0 1 1 1.697 1.697l-2.758 3.152 2.758 3.15a1.2 1.2 0 0 1 0 1.698z"
            />
          </svg>

          <span class="sm:inline">User is not verify yet</span>
        </div>
        <div
          v-if="is_user_verify == true"
          class="rounded-lg py-3 text-base text-green-700 inline-flex items-center w-full"
          role="alert"
        >
          <svg
            aria-hidden="true"
            focusable="false"
            data-prefix="fas"
            data-icon="check-circle"
            class="w-4 h-4 mr-2 fill-current"
            role="img"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 512 512"
          >
            <path
              fill="currentColor"
              d="M504 256c0 136.967-111.033 248-248 248S8 392.967 8 256 119.033 8 256 8s248 111.033 248 248zM227.314 387.314l184-184c6.248-6.248 6.248-16.379 0-22.627l-22.627-22.627c-6.248-6.249-16.379-6.249-22.628 0L216 308.118l-70.059-70.059c-6.248-6.248-16.379-6.248-22.628 0l-22.627 22.627c-6.248 6.248-6.248 16.379 0 22.627l104 104c6.249 6.249 16.379 6.249 22.628.001z"
            ></path>
          </svg>
          User is already verify
        </div>
      </div>
    </div>
  </div>
  <div
    class="flex justify-center color w-1/2 mx-auto rounded-b"
    v-if="is_user_verify == true"
  >
    <form action="" @submit.prevent="congrateUser()">
      <button class="font-sans font-semibold text-lg text-white uppercase">
        submit
      </button>
    </form>
  </div>
</template>

<script>
export default {
  props: ["first_name", "last_name", "is_user_verify"],
  data() {
    return {};
  },
  methods: {
    congrateUser() {
      this.$router.push("/congrate");
    },
  },
};
</script>

<style scoped>
.color {
  background: #2eade2;
}
.border-top-color {
  border-top: #2eade2 solid 2px;
}
</style>
