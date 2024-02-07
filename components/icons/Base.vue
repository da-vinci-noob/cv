<script setup>
// const Facebook = resolveComponent('icons/Facebook')
// Props
const props = defineProps({
  viewBox: { type: String, default: '0 0 24 24' },
  iconName: { type: String, default: '' },
  className: { type: String, default: '' }
})
const Github = resolveComponent('icons/Github')
const Email = resolveComponent('icons/Email')
const Phone = resolveComponent('icons/Phone')
const Globe = resolveComponent('icons/Globe')
const LinkedIn = resolveComponent('icons/LinkedIn')
</script>

<template>
  <svg
    :class="className"
    xmlns="http://www.w3.org/2000/svg"
    fill="none"
    aria-hidden="true"
    :viewBox="viewBox"
    :aria-labelledby="iconName"
  >
    <title :id="iconName" lang="en">{{ iconName }}</title>
    <component :is="Github" v-if="iconName == 'Github'" />
    <component :is="Email" v-if="iconName == 'Email'" />
    <component :is="Globe" v-if="iconName == 'Globe'" />
    <component :is="Phone" v-if="iconName == 'Phone'" />
    <component :is="LinkedIn" v-if="iconName == 'LinkedIn'" />
  </svg>
</template>
