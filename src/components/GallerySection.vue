<template>
  <section class="py-20 bg-white">
    <div class="container mx-auto px-6">
      <h2 class="text-4xl font-bold text-center mb-16 text-transparent bg-clip-text bg-gradient-to-r from-pink-500 to-purple-600">
        宝宝对我的好
      </h2>
      
      <div class="grid grid-cols-2 md:grid-cols-3 gap-4">
        <div v-for="(photo, index) in photos" :key="index" 
             class="relative overflow-hidden rounded-xl shadow-md hover:shadow-xl transition-all duration-300 group"
             :class="{'md:row-span-2': index === 1, 'md:col-span-2': index === 3}">
          <!-- 使用动态图片路径 -->
          <img 
            :src="photo.path" 
            :alt="photo.caption" 
            class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
          />
          <div class="absolute inset-0 bg-black bg-opacity-30 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300">
            <span class="text-white font-bold text-lg">{{ photo.caption }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// 假设您的图片命名为photo1.jpg到photo5.jpg
const photos = [
  { 
    caption: '宝宝给我买的大甜西瓜！',
    path: new URL('../assets/photo/4.JPG', import.meta.url).href
  },
  { 
    caption: '宝宝特别喜欢我的小礼物~',
    path: new URL('../assets/photo/2.jpg', import.meta.url).href
  },
  { 
    caption: '宝宝挂我在朋友圈里 第一次被这样在乎',
    path: new URL('../assets/photo/3.PNG', import.meta.url).href
  },
  { 
    caption: '宝宝给我点的甜点！',
    path: new URL('../assets/photo/1.jpg', import.meta.url).href
  },
  { 
    caption: '宝宝送的大樱桃！',
    path: new URL('../assets/photo/5.JPG', import.meta.url).href
  }
]
</script>

<style scoped>
/* 添加一些图片悬停效果 */
img {
  transition: transform 0.5s ease, filter 0.3s ease;
}

.group:hover img {
  filter: brightness(0.9);
}
</style>