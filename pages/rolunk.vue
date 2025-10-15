<script setup>
useHead({
  title: 'Rólunk',
})
</script>

<template>
  <div class="subpage-content about-us-content subpage-footer-content">
    <FleetSection />
  </div>
</template>

<style lang="scss" scoped>
.about-us-content {
  background: #ff6a00;
  padding: 1.5em;
  border-radius: 1em;
}

@media (max-width: 769px) {
  .about-us-content {
    padding: .7em .7em 1em .7em;
    border-radius: 1em;
  }
}
</style>
