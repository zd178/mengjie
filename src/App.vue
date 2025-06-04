<template>
  <div
    class="min-h-screen font-sans bg-gradient-to-b from-pink-50 to-purple-50"
  >
    <div class="fixed bottom-4 right-4 z-50">
      <button
        @click="toggleMusic"
        class="p-3 bg-pink-500 text-white rounded-full shadow-lg hover:bg-pink-600 transition-all"
        :class="{ 'animate-pulse': isPlaying }"
      >
        <svg
          v-if="!isPlaying"
          class="w-6 h-6"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M15.536 8.464a5 5 0 010 7.072m2.828-9.9a9 9 0 010 12.728M5.586 15.536a5 5 0 001.414 1.414m2.828-9.9a9 9 0 012.728-2.728"
          ></path>
        </svg>
        <svg
          v-else
          class="w-6 h-6"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M5 15l7-7 7 7"
          ></path>
        </svg>
      </button>
    </div>
    <HeroSection />
    <OurStory />
    <LoveLetter />
    <GallerySection />
    <FooterNote />

    <audio ref="audioPlayer" loop>
      <source :src="musicUrl" type="audio/mpeg" />
      您的浏览器不支持音频元素。
    </audio>
    <!-- 漂浮爱心 -->
    <div v-for="n in 15" :key="n" class="floating-heart" :style="heartStyle(n)">
      ❤️
    </div>

    <!-- 烟花效果 -->
    <div v-if="showFireworks" class="fireworks-container">
      <div
        v-for="n in 30"
        :key="'firework' + n"
        class="firework"
        :style="fireworkStyle(n)"
      ></div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import HeroSection from "./components/HeroSection.vue";
import OurStory from "./components/OurStory.vue";
import LoveLetter from "./components/LoveLetter.vue";
import GallerySection from "./components/GallerySection.vue";
import FooterNote from "./components/FooterNote.vue";

const showFireworks = ref(false);
import musicUrl from './assets/music/music.mp3'

const audioPlayer = ref(null)
// 漂浮爱心样式
const heartStyle = (n) => {
  return {
    left: `${Math.random() * 100}%`,
    top: `${Math.random() * 100}%`,
    fontSize: `${Math.random() * 20 + 10}px`,
    opacity: Math.random() * 0.5 + 0.3,
    animation: `float ${Math.random() * 10 + 10}s linear infinite`,
    animationDelay: `${Math.random() * 5}s`,
  };
};

// 烟花样式
const fireworkStyle = (n) => {
  const colors = ["#ff6b9d", "#ff8e53", "#ffcc00", "#a162e8", "#4facfe"];
  return {
    left: `${Math.random() * 100}%`,
    top: `${Math.random() * 100}%`,
    backgroundColor: colors[Math.floor(Math.random() * colors.length)],
    width: `${Math.random() * 6 + 2}px`,
    height: `${Math.random() * 6 + 2}px`,
    animation: `firework ${Math.random() * 3 + 2}s ease-out forwards`,
    animationDelay: `${Math.random() * 2}s`,
  };
};

// 页面加载后随机触发烟花
onMounted(() => {
  setInterval(() => {
    showFireworks.value = true;
    setTimeout(() => {
      showFireworks.value = false;
    }, 2000);
  }, 10000);
});

const isPlaying = ref(false);

const toggleMusic = () => {
  if (isPlaying.value) {
    audioPlayer.value.pause();
  } else {
    audioPlayer.value
      .play()
      .then(() => {
        isPlaying.value = true;
      })
      .catch((error) => {
        console.error("自动播放被阻止:", error);
        // 可以在这里添加用户交互后手动播放的逻辑
      });
  }
  isPlaying.value = !isPlaying.value;
};
</script>

<style>
/* 全局动画 */
@keyframes float {
  0% {
    transform: translateY(0) rotate(0deg);
  }
  100% {
    transform: translateY(-100vh) rotate(360deg);
  }
}

@keyframes firework {
  0% {
    transform: translate(0, 0);
    opacity: 1;
  }
  100% {
    transform: translate(var(--tx), var(--ty));
    opacity: 0;
  }
}

.floating-heart {
  position: fixed;
  pointer-events: none;
  z-index: 10;
}

.fireworks-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 20;
}

.firework {
  position: absolute;
  border-radius: 50%;
  --tx: calc(var(--x) * 1px);
  --ty: calc(var(--y) * 1px);
  animation: firework 2s ease-out forwards;
}
</style>