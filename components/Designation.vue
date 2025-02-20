<script setup>
const props = defineProps({
  user: Object
})
</script>

<template>
  <div>
    <div id="title" class="flex items-center justify-between">
      <div class="flex-1 space-y-2">
        <h1 id="name" class="heading">{{ user?.name }}</h1>
        <div class="details">
          <p id="desciption" class="content">
            {{ user?.description }}
          </p>
          <div
            id="location"
            v-if="user?.location?.title"
            class="flex space-x-1 font-mono text-xs muted mt-2 print:text-[10px]"
          >
            <div id="icon">
              <icons-base
                class="w-4 h-auto"
                iconName="Globe"
                viewBox="0 0 21 20"
              >
              </icons-base>
            </div>
            <a
              :href="
                user?.location?.link ||
                `https://www.google.com/maps/search/${user?.location?.title}`
              "
            >
              {{ user?.location?.title }}
            </a>
          </div>
        </div>
        <div id="social-links">
          <div
            id="print"
            class="print:block hidden font-mono text-xs mt-1 space-y-0.5 print:text-[10px]"
          >
            <div v-if="user?.contact?.phone">
              Phone:
              <a :href="`tel:${user?.contact?.phone}`" class="muted">
                {{ user?.contact?.phone }}
              </a>
            </div>
            <div v-if="user?.contact?.email">
              Email:
              <a :href="`mailto:${user?.contact?.email}`" class="muted">
                {{ user?.contact?.email }}
              </a>
            </div>
            <div v-for="item in user?.contact?.social" :key="item.name">
              {{ item.name }}:
              <a
                :href="item.url"
                target="_blank"
                rel="noreferrer"
                class="muted"
              >
                {{ item.url }}
              </a>
            </div>
          </div>
          <div id="web" class="flex flex-row space-x-2 print:hidden">
            <a
              class="flex items-center justify-center rounded-md text-sm print:text-xs text-gray-500 font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50 border border-gray-200 bg-background hover:bg-gray-100 hover:text-gray-800 size-8"
              :href="`mailto:${user?.contact?.email}`"
            >
              <icons-base
                class="w-4 h-auto"
                iconName="Email"
                viewBox="0 0 20 16"
              >
              </icons-base>
            </a>
            <a
              class="flex items-center justify-center rounded-md text-sm print:text-xs text-gray-500 font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50 border border-gray-200 bg-background hover:bg-gray-100 hover:text-gray-800 size-8"
              :href="`tel:${user?.contact?.phone}`"
            >
              <icons-base
                class="w-4 h-auto"
                iconName="Phone"
                viewBox="0 0 18 18"
              >
              </icons-base>
            </a>
            <a
              v-for="item in user?.contact?.social"
              :key="item.name"
              class="flex items-center justify-center rounded-md text-sm print:text-xs text-gray-500 font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50 border border-gray-200 bg-background hover:bg-gray-100 hover:text-gray-800 size-8"
              :href="item.url"
              target="_blank"
              rel="noreferrer"
            >
              <icons-base
                class="w-4 h-auto fill-current"
                :icon-name="item.name"
                viewBox="0 0 22 22"
              >
              </icons-base>
            </a>
          </div>
        </div>
      </div>

      <div
        id="avatar"
        class="relative h-28 w-28 flex shrink-0 overflow-hidden rounded-xl print:hidden"
      >
        <img class="h-full w-full aspect-square" :src="user?.avatar" alt="" />
      </div>
    </div>
  </div>
</template>
