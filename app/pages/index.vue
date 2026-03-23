<script setup>
import { ref, computed } from "vue"
import eventsData from "~/assets/events.json"

const showAllEvents = ref(false)
const searchQuery = ref("")

const filteredEvents = computed(() => {
  let events = eventsData

  // Filter by district if not showing all
  if (!showAllEvents.value) {
    events = events.filter((event) => event.District && event.District.includes("NJ-7"))
  }

  // Filter by search query if provided
  if (searchQuery.value.trim()) {
    const query = searchQuery.value.toLowerCase()
    events = events.filter(
      (event) =>
        event["Event Name"]?.toLowerCase().includes(query) ||
        event.Town?.toLowerCase().includes(query) ||
        event.District?.toLowerCase().includes(query)
    )
  }

  return events
})

const toggleView = () => {
  showAllEvents.value = !showAllEvents.value
}

const clearSearch = () => {
  searchQuery.value = ""
}
</script>

<template>
  <div>
    <img
      src="/images/hero.jpg"
      alt="No Kings, No Keans! Finding Kean Fridays"
      class="w-full mb-16"
    />

    <section class="container mx-auto p-4 max-w-6xl">
      <div class="mb-6">
        <h1 class="text-center mb-4">Upcoming Events</h1>
        <h3 class="text-center mb-12">No Thrones. No Crowns. No Kings.</h3>

        <!-- Controls -->
        <div class="flex flex-col sm:flex-row gap-4 mb-6">
          <div class="relative flex-1">
            <input
              v-model="searchQuery"
              type="text"
              placeholder="Search by event name, town, or district..."
              class="w-full px-4 py-2 pr-10 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
            <button
              v-if="searchQuery"
              @click="clearSearch"
              class="absolute right-3 top-1/2 -translate-y-1/2 text-gray-400 hover:text-gray-600 transition-colors"
              aria-label="Clear search"
            >
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
                <path
                  fill-rule="evenodd"
                  d="M10 18a8 8 0 100-16 8 8 0 000 16zM8.707 7.293a1 1 0 00-1.414 1.414L8.586 10l-1.293 1.293a1 1 0 101.414 1.414L10 11.414l1.293 1.293a1 1 0 001.414-1.414L11.414 10l1.293-1.293a1 1 0 00-1.414-1.414L10 8.586 8.707 7.293z"
                  clip-rule="evenodd"
                />
              </svg>
            </button>
          </div>
          <button
            @click="toggleView"
            class="px-6 py-2 bg-black text-white rounded-lg hover:bg-gray-800 transition-colors whitespace-nowrap"
          >
            {{ showAllEvents ? "Show NJ-7 Only" : "Show All Events" }}
          </button>
        </div>
      </div>

      <!-- Events list -->
      <div class="grid gap-4">
        <a
          v-for="event in filteredEvents"
          :key="event['#']"
          :href="event['Event Link']"
          target="_blank"
          rel="noopener noreferrer"
          class="plain block bg-white border border-gray-200 rounded-lg p-4 hover:shadow-lg transition-shadow cursor-pointer no-underline"
        >
          <div class="flex flex-col sm:flex-row sm:items-start sm:justify-between gap-2">
            <div class="flex-1">
              <h3 class="text-xl font-semibold mb-2 text-gray-900">
                {{ event["Event Name"] }}
              </h3>
              <div class="space-y-1 text-gray-700">
                <p><strong>Location:</strong> {{ event.Town }}</p>
                <p><strong>District:</strong> {{ event.District }}</p>
                <p>
                  <strong>Time:</strong> {{ event.Start }}
                  {{ event.End ? `- ${event.End}` : "" }}
                </p>
              </div>
            </div>
            <span
              class="inline-block px-4 py-2 bg-sky-800 text-white rounded hover:bg-sky-700 transition-colors text-center whitespace-nowrap"
            >
              View Event
            </span>
          </div>
        </a>
      </div>

      <!-- No results message -->
      <div v-if="filteredEvents.length === 0" class="text-center py-12 text-gray-500">
        <p class="text-xl">No events found matching your search.</p>
      </div>
    </section>
  </div>
</template>

<style lang="scss" scoped>
.hero {
  background: url("/images/hero.jpg") no-repeat center center;
  background-size: cover;
  min-height: 500px;
}
</style>
