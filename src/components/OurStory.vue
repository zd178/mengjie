<template>
  <section class="py-20 bg-gradient-to-b from-white to-pink-50 relative overflow-hidden">
    <!-- 装饰元素 -->
    <div class="absolute top-0 left-0 w-full h-full opacity-10">
      <div class="absolute top-20 left-10 w-32 h-32 rounded-full bg-pink-300 blur-xl"></div>
      <div class="absolute bottom-10 right-10 w-40 h-40 rounded-full bg-purple-300 blur-xl"></div>
    </div>
    
    <div class="container mx-auto px-6">
      <h2 class="text-4xl font-bold text-center mb-16 text-transparent bg-clip-text bg-gradient-to-r from-pink-500 to-purple-600">
        我们的故事
      </h2>
      
      <div class="relative">
        <!-- 时间线 -->
        <div class="absolute left-1/2 h-full w-1 bg-gradient-to-b from-pink-400 to-purple-500 transform -translate-x-1/2 hidden md:block"></div>
        
        <div class="space-y-16">
          <div v-for="(item, index) in story" :key="item.date" 
               class="relative group" :class="{'md:pl-16': index % 2 === 0, 'md:pr-16': index % 2 !== 0}">
            <!-- 时间点标记 -->
            <div class="absolute left-1/2 transform -translate-x-1/2 md:left-auto md:right-0 md:translate-x-0 w-8 h-8 rounded-full bg-pink-500 border-4 border-white z-10 hidden md:block"
                 :class="{'md:right-auto md:left-0': index % 2 === 0}"></div>
            
            <!-- 内容卡片 -->
            <div class="bg-white p-6 rounded-xl shadow-lg transition-all duration-300 hover:shadow-xl hover:scale-105"
                 :class="{'md:text-right': index % 2 !== 0, 'md:-translate-x-16': index % 2 === 0, 'md:translate-x-16': index % 2 !== 0}">
              <div class="text-sm font-semibold text-pink-500 mb-2">{{ item.date }}</div>
              <h3 class="text-xl font-bold text-gray-800 mb-3">{{ item.title }}</h3>
              <p class="text-gray-600">{{ item.content }}</p>
              <div class="mt-4">
                <span class="inline-block px-3 py-1 text-xs font-semibold rounded-full bg-pink-100 text-pink-800">
                  {{ item.tag }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const story = [
  { 
    date: '2025.05.11', 
    title: '初见', 
    content: '那天正午遇见你，就被你完全吸引了',
    tag: '心动瞬间'
  },
  { 
    date: '2025.05.11', 
    title: '表白', 
    content: '第一次见面就光速决定在一起',
    tag: '勇敢表白'
  },
  { 
    date: '2025.05.15', 
    title: '送你一封情书', 
    content: '我为宝宝写了第一封情书，用文字写我的爱意。',
    tag: '爱的承诺'
  },
  { 
    date: '2025.05.18', 
    title: '朋友圈官宣', 
    content: '我和宝宝在朋友圈官宣，让我们的朋友们吃吃狗粮~',
    tag: '炫耀我的爱人'
  },
  { 
    date: '...', 
    title: '故事还在继续...', 
    content: '',
    tag: '我们会越来越好'
  }
]
</script>