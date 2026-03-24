<template>
  <div class="newsletter-signup w-fit">
    <h3 class="mb-4">Stay Informed</h3>
    <template v-if="!success">
      <p class="mb-4">
        Sign up for to help us Find Kean. We'll keep showing up, even if Tom Kean Jr
        doesn't.
      </p>
      <form @submit.prevent="handleSubmit">
        <div class="flex align-items-center gap-2 mb-3">
          <InputText
            v-model="email"
            type="email"
            placeholder="Enter your email"
            :disabled="isSubmitting"
            :invalid="!!error"
            required
          />
          <Button
            type="submit"
            label="Sign Up"
            :loading="isSubmitting"
            :disabled="isSubmitting || !email || !consent"
          />
        </div>
        <div class="flex align-items-center gap-2">
          <Checkbox v-model="consent" inputId="consent" :binary="true" />
          <label for="consent" class="text-sm text-gray-600">
            I consent to being occasionally bothered by the creators of this website.
          </label>
        </div>
      </form>
    </template>
    <Message v-if="success" severity="success" :closable="false" class="mt-3">
      {{ success }}
    </Message>

    <Message v-if="error" severity="error" :closable="false" class="mt-3">
      {{ error }}
    </Message>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()
const email = ref("")
const consent = ref(true)
const isSubmitting = ref(false)
const success = ref("")
const error = ref("")

const handleSubmit = async () => {
  if (!email.value) return

  // Reset messages
  success.value = ""
  error.value = ""
  isSubmitting.value = true

  try {
    const { error: insertError } = await supabase.from("email-list").insert({
      email: email.value,
      source: "finding-kean",
      district: "NJ-7",
    })

    if (insertError) {
      // Check if it's a duplicate email error
      if (insertError.code === "23505") {
        error.value = "This email is already subscribed."
      } else {
        error.value = "Failed to subscribe. Please try again."
      }
    } else {
      success.value = "Thank you for subscribing!"
      email.value = ""
    }
  } catch (err) {
    error.value = "An unexpected error occurred. Please try again."
    console.error("Newsletter signup error:", err)
  } finally {
    isSubmitting.value = false
  }
}
</script>
