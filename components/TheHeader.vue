<template>
  <header class="bg-white dark:bg-gray-800 shadow-sm">
    <div class="container mx-auto px-4 py-4">
      <div class="flex justify-between items-center">
        <NuxtLink to="/" class="text-2xl font-bold text-gray-800 dark:text-white">
          个人技术博客
        </NuxtLink>
        
        <nav class="hidden md:flex space-x-6">
          <NuxtLink to="/" class="text-gray-600 dark:text-gray-300 hover:text-gray-900 dark:hover:text-white">
            首页
          </NuxtLink>
          <NuxtLink to="/blog" class="text-gray-600 dark:text-gray-300 hover:text-gray-900 dark:hover:text-white">
            博客
          </NuxtLink>
          <NuxtLink to="/projects" class="text-gray-600 dark:text-gray-300 hover:text-gray-900 dark:hover:text-white">
            作品集
          </NuxtLink>
          <NuxtLink to="/about" class="text-gray-600 dark:text-gray-300 hover:text-gray-900 dark:hover:text-white">
            关于我
          </NuxtLink>
        </nav>
        
        <div class="flex items-center space-x-4">
          <button @click="toggleColorMode" class="text-gray-600 dark:text-gray-300 hover:text-gray-900 dark:hover:text-white">
            <span v-if="colorMode.value === 'dark'">🌞</span>
            <span v-else>🌙</span>
          </button>
          
          <button class="md:hidden text-gray-600 dark:text-gray-300" @click="isMenuOpen = !isMenuOpen">
            <span v-if="!isMenuOpen">☰</span>
            <span v-else>✕</span>
          </button>
        </div>
      </div>
      
      <!-- Mobile menu -->
      <div v-if="isMenuOpen" class="md:hidden mt-4 space-y-2">
        <NuxtLink to="/" class="block py-2 text-gray-600 dark:text-gray-300 hover:text-gray-900 dark:hover:text-white">
          首页
        </NuxtLink>
        <NuxtLink to="/blog" class="block py-2 text-gray-600 dark:text-gray-300 hover:text-gray-900 dark:hover:text-white">
          博客
        </NuxtLink>
        <NuxtLink to="/projects" class="block py-2 text-gray-600 dark:text-gray-300 hover:text-gray-900 dark:hover:text-white">
          作品集
        </NuxtLink>
        <NuxtLink to="/about" class="block py-2 text-gray-600 dark:text-gray-300 hover:text-gray-900 dark:hover:text-white">
          关于我
        </NuxtLink>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue';

const colorMode = useColorMode();
const isMenuOpen = ref(false);

const toggleColorMode = () => {
  colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark';
};
</script>
