<script setup>
const isFixed = ref(false);
const navWrapper = ref(null);
const navHeight = ref(0);
const activeSection = ref("");

const sections = [
  { id: "the-search", label: "The Search" },
  { id: "the-absence", label: "The Absence" },
  { id: "the-record", label: "The Record" },
  { id: "autopilot-rep", label: "Autopilot Rep" },
  { id: "toms-2-daddies", label: "Tom's 2 Daddies" },
];

const scrollTo = (id) => {
  const el = document.getElementById(id);
  if (el) el.scrollIntoView({ behavior: "smooth" });
};

onMounted(() => {
  const offsetTop = navWrapper.value?.offsetTop ?? 0;
  navHeight.value = navWrapper.value?.offsetHeight ?? 0;

  const handleScroll = () => {
    isFixed.value = window.scrollY >= offsetTop;
  };

  window.addEventListener("scroll", handleScroll, { passive: true });

  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          activeSection.value = entry.target.id;
        }
      });
    },
    { rootMargin: "-10% 0px -80% 0px", threshold: 0 }
  );

  sections.forEach(({ id }) => {
    const el = document.getElementById(id);
    if (el) observer.observe(el);
  });

  onUnmounted(() => {
    window.removeEventListener("scroll", handleScroll);
    observer.disconnect();
  });
});
</script>

<template>
  <div ref="navWrapper" :style="isFixed ? { height: navHeight + 'px' } : {}">
    <nav :class="['section-nav', { 'section-nav--fixed': isFixed }]">
      <div class="stripe-bar" />
      <div class="nav-inner">
        <button
          v-for="section in sections"
          :key="section.id"
          :class="['nav-link', { active: activeSection === section.id }]"
          @click="scrollTo(section.id)"
        >
          {{ section.label }}
        </button>
      </div>
      <div class="stripe-bar" />
    </nav>
  </div>
</template>

<style lang="scss" scoped>
.section-nav {
  width: 100%;
  background: #1c1917;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.4);

  &.section-nav--fixed {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 50;
  }
}

.stripe-bar {
  height: 6px;
  background: repeating-linear-gradient(
    to right,
    #cc0000 0px,
    #cc0000 18px,
    #ffffff 18px,
    #ffffff 36px
  );
}

.nav-inner {
  display: flex;
  justify-content: flex-start;
  @media (min-width: 768px) {
    justify-content: center;
  }
  overflow-x: auto;
  scrollbar-width: none;
  &::-webkit-scrollbar {
    display: none;
  }
}

.nav-link {
  flex-shrink: 0;
  font-family: var(--font-family-header);
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: #d4d4d4;
  background: transparent;
  border: none;
  padding: 12px 20px;
  cursor: pointer;
  transition: all 0.2s ease;
  white-space: nowrap;

  &:hover {
    color: #ffffff;
    background: rgba(204, 0, 0, 0.3);
  }

  &.active {
    color: #ffffff;
    background: #cc0000;
  }
}
</style>
