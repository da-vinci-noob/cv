<script setup>
const config = useRuntimeConfig()
const user = useUserStore()
const userDetails = computed(() => {
  try {
    return (
      (config.public.user && JSON.parse(config.public.user)) ||
      user?.value ||
      null
    )
  } catch (SyntaxError) {
    return null
  }
})
</script>

<template>
  <div
    id="container"
    class="mx-auto scroll-my-12 overflow-auto p-4 print:p-2 md:p-16"
    v-if="userDetails"
  >
    <div class="mx-auto w-full max-w-2xl space-y-4 bg-white">
      <Designation :user="userDetails" :key="userDetails.name" />
      <About :user="userDetails" :key="userDetails.name" />
      <WorkExperience :user="userDetails" :key="userDetails.name" />
      <Education :user="userDetails" :key="userDetails.name" />
      <Skills :user="userDetails" :key="userDetails.name" />
      <Projects :user="userDetails" :key="userDetails.name" />
    </div>
  </div>
  <div v-else>
    <UploadUserDetails />
  </div>
</template>

<style>
@media print {
  * {
    -webkit-print-color-adjust: exact;
    print-color-adjust: exact;
  }
}
</style>
