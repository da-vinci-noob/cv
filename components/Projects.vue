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
                {{ project.title }}
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
            <div
              class="mt-2 flex gap-2 text-xs border-t border-gray-100 pt-2 print:hidden"
              v-if="project.sourceCode || project.liveDemo"
            >
              <a
                v-if="project.sourceCode"
                :href="project.sourceCode"
                class="inline-flex items-center bg-white border border-indigo-200 hover:border-indigo-300 px-2 py-1 rounded-md text-indigo-600 hover:text-indigo-700 hover:bg-indigo-50 transition-all duration-200 text-[11px] font-medium"
                target="_blank"
                rel="noreferrer"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="w-3 h-3 mr-1"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path
                    d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"
                  ></path>
                </svg>
                Source Code
              </a>
              <a
                v-if="project.liveDemo"
                :href="project.liveDemo"
                class="inline-flex items-center bg-white border border-indigo-200 hover:border-indigo-300 px-2 py-1 rounded-md text-indigo-600 hover:text-indigo-700 hover:bg-indigo-50 transition-all duration-200 text-[11px] font-medium"
                target="_blank"
                rel="noreferrer"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="w-3 h-3 mr-1"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path
                    d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"
                  ></path>
                  <polyline points="15 3 21 3 21 9"></polyline>
                  <line x1="10" y1="14" x2="21" y2="3"></line>
                </svg>
                Live Demo
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
