<script setup>
const props = defineProps({
  user: Object
})

// Parsing date for sorting
props?.user?.workExp?.forEach(function (obj) {
  obj.parsedDate = new Date(`01 ${obj.startMonth} ${obj.startYear}`)
})

const sortedUserExperience = computed(() => {
  return props?.user?.workExp?.sort((a, b) => b.parsedDate - a.parsedDate)
})
</script>

<template>
  <div>
    <div id="work-experience">
      <h1 id="work-experience-heading" class="heading">Work Experience</h1>
      <div>
        <div
          :id="`Company_${index + 1}`"
          class="pt-1"
          v-for="(work, index) in sortedUserExperience"
          :key="work.company"
        >
          <div
            id="title"
            class="work-exp-sub-heading flex justify-between mt-2"
          >
            <div class="flex sm:items-center items-start">
              {{ work.company }}
              <div class="ml-2 sm:w-auto w-full flex flex-wrap gap-2">
                <div
                  v-for="badge in work.badges.filter((n) => n)"
                  :key="badge"
                  class="text-xs"
                >
                  <span class="bg-gray-200 px-2 py-1 rounded-md">
                    {{ badge }}
                  </span>
                </div>
              </div>
            </div>
            <div id="period" class="content font-normal whitespace-nowrap">
              {{ work.startMonth }} {{ work.startYear }} -
              {{
                work.endYear
                  ? work.endMonth.concat(' ', work.endYear)
                  : 'Present'
              }}
            </div>
          </div>
          <div id="position" class="content tracking-wide opacity-80 mt-1">
            {{ work.position }}
          </div>
          <div id="description" class="content mt-2 text-xs">
            {{ work.description }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
