<template>
  <div class="grid grid-cols-1 md:grid-cols-3 gap-4 w-full">
    <div class="bg-white rounded-lg shadow h-full flex flex-col"
    v-for="product in products" :key="product.id">
      <img :src="product.image" class="w-full h-40 object-cover rounded-t-lg">
      <div class="p-4 flex-grow flex flex-col justify-between">
        <h5 class="text-lg font-semibold mb-2">{{ product.name }}</h5>
        <p class="text-gray-700 mb-2">{{ product.description }}</p>
        <p class="font-bold text-blue-600 mb-4">$ {{ product.price }}</p>
        <button class="bg-green-500 hover:bg-green-600 text-white py-2 px-4 rounded w-full"
        @click="handleAddCart(product)"> 加入購物車 </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { inject } from 'vue'


defineProps ({
  products:{
    type: Array,
    required: true,
  },
})
const emit =defineEmits (['add-cart'])
const handleAddCart = (product) => {
  emit('add-cart', product)
  showNotification(`商品 ${product.name}已加入購物歌`, 'info')
}

const showNotification = inject('showNotification')
</script>
