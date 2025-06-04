<template>
  <footer class="py-12 bg-gradient-to-b from-pink-200 to-pink-300 text-center relative overflow-hidden">
    <!-- 装饰元素 -->
    <div class="absolute top-0 left-0 w-full h-full opacity-20">
      <div class="absolute top-1/4 left-1/4 w-24 h-24 rounded-full bg-white blur-xl"></div>
      <div class="absolute bottom-1/3 right-1/3 w-32 h-32 rounded-full bg-pink-100 blur-xl"></div>
    </div>
    
    <div class="relative z-10">
      <p class="text-xl md:text-2xl font-light text-pink-800 mb-6">"愿时光缓缓，我的爱不散。"</p>
      
      <div class="flex justify-center space-x-6">
        <button class="px-6 py-2 bg-white text-pink-600 rounded-full shadow-md hover:shadow-lg transition-all hover:scale-105">
          给我一个拥抱
        </button>
        <button 
          class="px-6 py-2 bg-pink-600 text-white rounded-full shadow-md hover:shadow-lg transition-all hover:scale-105"
          @click="showConfetti">
          我也爱你
        </button>
      </div>
      
      <div class="mt-8 text-pink-700 text-sm">
        <p>© 2025 献给世界上最美的唐婕</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
const showConfetti = () => {
  // 这里可以添加彩带效果
  alert('唐婕，谢谢你接受我的爱！❤️')
}
</script>