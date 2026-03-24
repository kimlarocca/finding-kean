<script setup>
import NewsletterSignup from "./NewsletterSignup.vue"

const currentYear = new Date().getFullYear()
</script>

<template>
  <div class="container p-4">
    <Divider class="mb-12" />
    <footer>
      <div class="container">
        <NewsletterSignup />
        <Divider class="my-12" />
        <p class="small">
          The views expressed herein are exclusively those of the authors and do not
          reflect the official stance of any political candidate or other organization and
          have not been requested or endorsed by any related entity. Information presented
          has been verified as accurate to the best of our ability. This website was not
          requested or authorized by any candidate or candidate's committee. Paid for by
          People Are People LLC, 971 US Highway 202N #8014, Branchburg, NJ 08876.
        </p>
        <p class="small mt-2">
          Copyright © {{ currentYear }} People Are People NJ. All Rights Reserved.
        </p>
      </div>
    </footer>
  </div>
</template>
