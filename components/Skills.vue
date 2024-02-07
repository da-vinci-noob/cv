<script setup>
const props = defineProps({
  user: Object
})
</script>

<template>
  <div>
    <div id="skills">
      <h1 id="skills-heading" class="heading">Skills</h1>
      <div
        id="skill-badges"
        class="flex text-xs font-semibold font-mono mt-3 flex-wrap gap-1"
      >
        <div
          v-for="(skill, index) in user?.skills"
          :key="skill"
          :id="`skill_${index + 1}`"
        >
          <a
            :href="`https://www.google.com/search?q=${skill}`"
            target="_blank"
            rel="noreferrer"
            class="inline-flex items-center rounded-md border px-2 py-0.5 transition-colors focus:outline-none focus:ring-2 focus:ring-ring focus:ring-offset-2 text-nowrap border-transparent bg-gray-700 text-gray-100 hover:bg-gray-600 cursor-pointer hover:text-white whitespace-nowrap"
          >
            {{ skill }}
          </a>
        </div>
      </div>
    </div>
  </div>
</template>
