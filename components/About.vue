<script setup>
const props = defineProps({
  user: Object
})
</script>

<template>
  <div id="about" v-if="user?.about">
    <h1 id="about-heading" class="heading">About</h1>
    <div id="about-description" class="content mt-2">
      {{ user.about }}
    </div>
  </div>
</template>
