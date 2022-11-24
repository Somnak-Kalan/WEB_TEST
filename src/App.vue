<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>
<template>
  <div class="navigationbar p-0 m-0">
    <div class="container mx-auto">
      <div class="flex justify-around">
        <div class="m-2">
          <img width="100" src="@/assets/images/bidnow-logo.png " alt="" />
        </div>
        <nav class="flex justify-center">
          <ul class="flex justify-between">
            <li class="m-2 mx-8">
              <RouterLink to="/">Home</RouterLink>
            </li>
            <li class="m-2 mx-8">
              <RouterLink to="/about">About</RouterLink>
            </li>
            <li class="m-2 mx-8">
              <RouterLink to="/search">search</RouterLink>
            </li>
          </ul>
        </nav>
      </div>
    </div>
  </div>
  <div class="container">
    <main>
      <RouterView />
    </main>
  </div>
</template>
<style>
.container {
  width: 80%;
  margin: auto;
}
.navigationbar {
  background: #2eade2;
  margin: 0;
  padding: 0;
}
</style>
