<script setup lang="ts">
import Dropdowns from "@/components/Dropdowns.vue";
</script>

<template>
  <nav class="navbar navbar-light bg-light">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">
        <img
          :src="require('@/assets/logo.png')"
          alt=""
          width="30"
          height="30"
          class="d-inline-block align-top"
        />
        Vue3.2
      </a>
      <Dropdowns></Dropdowns>
    </div>
  </nav>
</template>

<style scoped></style>
