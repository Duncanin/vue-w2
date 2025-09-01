<template>
  <div class="fixed top-0 right-0 p-3 z-[1050]"
  v-if="notificationState.isShow">
    <div class="flex items-center text-white rounded shadow p-3"
    :class="bgColorClass">
      <div class="d-flex">
        <div class="mr-4">{{ notificationState.message }}</div>
        <button type="button" class="ml-auto text-white"></button>
      </div>
    </div>
  </div>
</template>

<script setup>
import {inject, computed} from 'vue';

const notificationState = inject('notificationState')
const bgColorClass = computed(() => {
  switch (notificationState.type) {
    case 'error':
      return 'bg-red-500 opacity-90'
    case 'success':
      return 'bg-green-500 opacity-90'
    case 'info':
    default:
      return 'bg-blue-500 opacity-70'
  }
})
</script>
