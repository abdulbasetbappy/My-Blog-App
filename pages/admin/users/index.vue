<template>
    <div>
    <!-- breadcrumb -->
    <nav class="text-sm font-semibold mb-6" aria-label="Breadcrumb">
      <ol class="list-none p-0 inline-flex">
        <li class="flex items-center text-blue-500">
          <NuxtLink href="#" class="text-gray-700">Admin</NuxtLink>
          <Icon name="uil:arrow-right"/>  
        </li>
        <li class="flex items-center">
          <NuxtLink href="#" class="text-gray-700">Users</NuxtLink>
        </li>
      </ol>
    </nav>
    <!-- breadcrumb end -->
<UserDetailsTable/>


  </div>
</template>

<script setup lang="ts">
import UserDetailsTable from '~/components/UserDetailsTable.vue';

definePageMeta({
  layout: 'admin',
  middleware: 'auth'
})
</script>

<style scoped>

</style>