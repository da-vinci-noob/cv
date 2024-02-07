<script setup>
const props = defineProps({
  user: Object
})

const sortedUserEducations = computed(() => {
  return props?.user?.education?.sort((a, b) => b.startYear - a.startYear)
})
</script>

<template>
  <div>
    <div id="education">
      <h1 id="education-heading" class="heading">Education</h1>
      <div
        :id="`Education_${index + 1}`"
        class="mt-2"
        v-for="(education, index) in sortedUserEducations"
        :key="education.school"
      >
        <div id="university" class="flex justify-between">
          <div class="work-exp-sub-heading">
            {{ education.school }}
          </div>
          <div id="range" class="content font-normal">
            {{ education.startYear }} - {{ education.endYear }}
          </div>
        </div>
        <div id="degree" class="content mt-1">
          {{ education.degree }}
        </div>
      </div>
    </div>
  </div>
</template>
