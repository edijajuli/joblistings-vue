<script setup>
import logo from "@/assets/img/logo.png";
</script>

<template>
  <footer class="bg-green-700 py-4 mt-auto">
    <div
      class="container mx-auto flex flex-col md:flex-row items-center justify-center px-4"
    >
      <div class="mb-4 md:mb-0">
        <img :src="logo" alt="Logo" class="h-6 w-auto mr-2" />
      </div>
      <div>
        <p class="text-sm text-white mt-2 md:mt-0">
          Copyright &copy; 2024 JobListings. All rights reserved.
        </p>
      </div>
    </div>
  </footer>
</template>
