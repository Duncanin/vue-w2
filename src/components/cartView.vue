<template>
  <div class="w-full px-2">
    <h2 class="mb-3">購物車</h2>
    <div v-if="carts.length===0" class="font-normal text-gray">購物車是空的</div>
    <ul class="space-y-3 mb-3">
      <li class="flex justify-between items-center bg-white p-4 rounded shadow"
      v-for="i in carts" :key="i.id">
        <div>
          <h6 class="my-0">{{ i.name }}</h6>
          <small class="text-gray-500">數量：{{ i.quantity }}</small>
        </div>
        <div>
          <span class="text-gray-500">$ {{ i.price*i.quantity }}</span>
          <button class="ml-2 text-red-600 hover:text-red-800 text-sm"
          @click="handleRemoveCart(i)">移除</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script setup>
defineProps ({
  carts: {
    type: Array,
    required: true,
  }
})

const emit = defineEmits (['remove-cart'])
import { inject } from 'vue'
const showNotification = inject('showNotification')
const handleRemoveCart = (i)=> {
  emit('remove-cart', i)
  showNotification(`已移除 ${i.name}`, 'error')
}
</script>
