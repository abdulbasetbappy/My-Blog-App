<script setup>
const Blogs = ref([]);
//onmounted get all data from /api/post
onMounted(async () => {
    const response = await fetch('/api/post');
    const data = await response.json();
    Blogs.value = data;
    console.log(Blogs.value);
});
</script>
<template>
  <div
    class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-5 mt-5 md:mt-10"
  >
    <div
      v-for="Blog in Blogs"
      :key="Blog._id"
      class="bg-white shadow-md rounded-lg overflow-hidden"
    >
      <div class="rounded-t-md overflow-hidden">
        <img
          :src="Blog.imageData"
          alt="Post Image"
          class="transition-transform rounded-t-md hover:scale-110"
        />
      </div>

      <div class="p-4">
        <span class="text-primary text-sm">{{ Blog.status }}</span>
        <h2 class="text-xl font-bold mt-2">{{ Blog.title }}</h2>
        <span class="font-bold text-gray-500">By</span> {{ Blog.user || "Admin" }}
        <p class="text-gray-700 mt-2">
          {{ Blog.description }}
          <NuxtLink :to="`/blogs/${Blog._id}`" class="text-primary cursor-pointer"
            >See more
          </NuxtLink>
        </p>
        <div class="flex items-center justify-between my-5">
          <div class="flex items-center">
            <Icon name="system-uicons:calendar-date"></Icon>
            <p class="text-gray-600 text-sm ml-2">{{ Blog.createdAt }}</p>
            <span class="mx-1">|</span>
            <Icon name="lets-icons:view-fill"></Icon>
            <p class="text-gray-600 text-sm ml-2">{{ Blog.view || "320" }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
