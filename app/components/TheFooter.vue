<script setup>
const currentYear = new Date().getFullYear()
</script>

<template>
  <div class="container p-4">
    <Divider class="my-12" />
    <footer>
      <p class="small text-center">
        This website is a work of satire and political commentary. We are not affiliated
        with, sponsored by, or endorsed by any of the companies whose logos appear here.
      </p>
      <p class="small mt-2 text-center">
        Copyright © {{ currentYear }}. All Rights Reserved.
      </p>
    </footer>
  </div>
</template>
