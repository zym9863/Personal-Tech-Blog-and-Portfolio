<template>
  <div>
    <div class="max-w-4xl mx-auto">
      <h1 class="text-3xl md:text-4xl font-bold mb-6 text-black dark:text-black">博客文章</h1>
      
      <!-- Filter and Search -->
      <div class="mb-8 bg-white dark:bg-gray-800 p-4 rounded-lg shadow">
        <div class="flex flex-col md:flex-row gap-4">
          <div class="flex-grow">
            <input 
              v-model="searchQuery" 
              type="text" 
              placeholder="搜索文章..." 
              class="w-full px-4 py-2 border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 bg-white dark:bg-gray-700 text-gray-900 dark:text-white"
            />
          </div>
          <div>
            <select 
              v-model="selectedTag" 
              class="w-full md:w-auto px-4 py-2 border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 bg-white dark:bg-gray-700 text-gray-900 dark:text-white"
            >
              <option value="">所有标签</option>
              <option v-for="tag in allTags" :key="tag" :value="tag">{{ tag }}</option>
            </select>
          </div>
        </div>
      </div>
      
      <!-- Blog Posts -->
      <div v-if="filteredPosts.length > 0" class="space-y-8">
        <div v-for="post in filteredPosts" :key="post._path" class="bg-white dark:bg-gray-800 rounded-lg shadow overflow-hidden">
          <NuxtLink :to="post._path" class="block hover:opacity-90 transition">
            <div class="md:flex">
              <div v-if="post.image" class="md:w-1/3">
                <img :src="post.image" :alt="post.title" class="w-full h-48 md:h-full object-cover">
              </div>
              <div class="p-6 md:w-2/3">
                <div class="flex items-center text-sm text-gray-500 dark:text-gray-400 mb-2">
                  <span>{{ formatDate(post.date) }}</span>
                  <span class="mx-2">•</span>
                  <span>{{ post.readingTime || '5 分钟阅读' }}</span>
                </div>
                <h2 class="text-xl md:text-2xl font-semibold mb-2 text-gray-800 dark:text-white">{{ post.title }}</h2>
                <p class="text-gray-600 dark:text-gray-300 mb-4">{{ post.description }}</p>
                <div class="flex flex-wrap gap-2">
                  <span v-for="tag in post.tags" :key="tag" class="bg-blue-100 dark:bg-blue-900 text-blue-800 dark:text-blue-100 text-xs px-3 py-1 rounded-full">
                    {{ tag }}
                  </span>
                </div>
              </div>
            </div>
          </NuxtLink>
        </div>
      </div>
      
      <!-- No Results -->
      <div v-else class="text-center py-12">
        <p class="text-gray-600 dark:text-gray-400 text-lg">没有找到符合条件的文章</p>
        <button @click="resetFilters" class="mt-4 text-blue-600 dark:text-blue-400 font-medium">
          重置筛选条件
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import { formatDate } from '~/utils/date';

// Fetch all blog posts
const { data: posts } = await useAsyncData('posts', () => 
  queryContent('blog')
    .sort({ date: -1 })
    .find()
);

// Search and filter functionality
const searchQuery = ref('');
const selectedTag = ref('');

// Get all unique tags
const allTags = computed(() => {
  const tags = new Set();
  posts.value.forEach(post => {
    if (post.tags && Array.isArray(post.tags)) {
      post.tags.forEach(tag => tags.add(tag));
    }
  });
  return Array.from(tags);
});

// Filter posts based on search query and selected tag
const filteredPosts = computed(() => {
  let filtered = posts.value;
  
  if (searchQuery.value) {
    const query = searchQuery.value.toLowerCase();
    filtered = filtered.filter(post => 
      post.title.toLowerCase().includes(query) || 
      post.description.toLowerCase().includes(query)
    );
  }
  
  if (selectedTag.value) {
    filtered = filtered.filter(post => 
      post.tags && post.tags.includes(selectedTag.value)
    );
  }
  
  return filtered;
});

// Reset filters
const resetFilters = () => {
  searchQuery.value = '';
  selectedTag.value = '';
};
</script>
