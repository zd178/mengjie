<template>
  <section
    class="relative h-screen flex flex-col justify-center items-center text-center overflow-hidden"
  >
    <!-- 背景图片与遮罩 -->
    <div class="absolute inset-0 bg-cover bg-center" :style="{ backgroundImage: `url(/src/assets/bg.jpg)` }"></div>
    <div class="absolute inset-0 bg-black bg-opacity-40"></div>
    
    <!-- 内容 -->
    <div class="relative z-10 px-4">
      <h1 class="text-4xl md:text-6xl font-bold text-white drop-shadow-lg mb-6 animate-fade-in">
        写给唐婕的温柔时光
      </h1>
      <p class="text-xl md:text-2xl text-pink-200 font-light mb-8 animate-fade-in animate-delay-200">
        "她是我此生最温柔的注目"
      </p>
      
      <!-- 向下箭头 -->
      <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 animate-bounce">
        <svg class="w-10 h-10 text-pink-200" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path>
        </svg>
      </div>
    </div>
    
    <!-- 飘落花瓣 -->
    <div v-for="n in 15" :key="n" class="absolute petal" :style="petalStyle(n)">
      <svg viewBox="0 0 20 20" class="w-6 h-6">
        <path fill="rgba(255,255,255,0.7)" d="M10,1.5c-4.7,0-8.5,3.8-8.5,8.5s3.8,8.5,8.5,8.5s8.5-3.8,8.5-8.5S14.7,1.5,10,1.5z M10,17.5c-4.1,0-7.5-3.4-7.5-7.5S5.9,2.5,10,2.5s7.5,3.4,7.5,7.5S14.1,17.5,10,17.5z"/>
      </svg>
    </div>
  </section>
</template>

<script setup>
const petalStyle = (n) => {
  return {
    left: `${Math.random() * 100}%`,
    top: `${Math.random() * 100}%`,
    opacity: Math.random() * 0.7 + 0.3,
    transform: `rotate(${Math.random() * 360}deg)`,
    animation: `fall ${Math.random() * 10 + 5}s linear infinite`,
    animationDelay: `${Math.random() * 5}s`
  }
}
</script>

<style>
@keyframes fall {
  to {
    transform: translateY(100vh) rotate(360deg);
  }
}

@keyframes fade-in {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in {
  animation: fade-in 1.5s ease-out forwards;
}

.animate-delay-200 {
  animation-delay: 0.2s;
}

.petal {
  pointer-events: none;
  z-index: 5;
}
</style>