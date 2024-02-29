<script setup>
const props = defineProps({
  user: Object
})

const goToSite = (url) => {
  if (url) {
    window.open(url, '_blank')
  }
}
</script>

<template>
  <div>
    <div id="projects" class="pb-12">
      <h1 id="projects-heading" class="heading">Projects</h1>
      <div
        class="-mx-2 mt-3 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-3 print:grid-cols-3"
      >
        <div
          v-for="project in user?.projects"
          :key="project.title"
          class="border border-gray-100 rounded-lg px-2 py-3"
        >
          <div
            id="project-card"
            class="flex flex-col overflow-hidden h-full justify-between"
          >
            <div class="flex flex-col space-y-1.5">
              <div class="work-exp-sub-heading leading-tight">
                <a
                  v-if="project.url"
                  id="project-title"
                  :href="project.url"
                  class="cursor-pointer underline"
                  target="_blank"
                  rel="noreferrer"
                >
                  {{ project.title }}
                </a>
                <div v-else>{{ project.title }}</div>
              </div>
              <div id="project-description" class="content text-xs">
                {{ project.description }}
              </div>
            </div>
            <div id="badges" class="flex text-gray-700 font-semibold font-mono">
              <div class="mt-2 flex flex-wrap gap-1">
                <div
                  v-for="(badge, index) in project.badges.filter((n) => n)"
                  :key="badge"
                  :id="`project-badge_${index + 1}`"
                  class="inline-flex items-center rounded-md border transition-colors focus:outline-none focus:ring-2 focus:ring-ring focus:ring-offset-2 text-nowrap border-transparent bg-gray-100 hover:bg-secondary/60 px-1 py-0 text-[10px]"
                >
                  {{ badge }}
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
