<template>
  <div>
    <div class="max-w-4xl mx-auto">
      <h1 class="text-3xl md:text-4xl font-bold mb-6 text-black dark:text-black">作品集</h1>
      
      <!-- Filter by Category -->
      <div class="mb-8">
        <div class="flex flex-wrap gap-2">
          <button 
            @click="selectedCategory = ''"
            :class="[
              'px-4 py-2 rounded-lg transition',
              selectedCategory === '' 
                ? 'bg-blue-600 text-white' 
                : 'bg-gray-100 dark:bg-gray-700 text-gray-800 dark:text-gray-200 hover:bg-gray-200 dark:hover:bg-gray-600'
            ]"
          >
            全部
          </button>
          <button 
            v-for="category in categories" 
            :key="category"
            @click="selectedCategory = category"
            :class="[
              'px-4 py-2 rounded-lg transition',
              selectedCategory === category 
                ? 'bg-blue-600 text-white' 
                : 'bg-gray-100 dark:bg-gray-700 text-gray-800 dark:text-gray-200 hover:bg-gray-200 dark:hover:bg-gray-600'
            ]"
          >
            {{ category }}
          </button>
        </div>
      </div>
      
      <!-- Projects Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div 
          v-for="project in filteredProjects" 
          :key="project._path" 
          class="bg-white dark:bg-gray-800 rounded-lg overflow-hidden shadow-md hover:shadow-lg transition"
        >
          <NuxtLink :to="project._path">
            <img 
              v-if="project.image" 
              :src="project.image" 
              :alt="project.title" 
              class="w-full h-56 object-cover"
            >
            <div class="p-6">
              <h2 class="text-xl font-semibold mb-2 text-gray-800 dark:text-white">{{ project.title }}</h2>
              <p class="text-gray-600 dark:text-gray-300 mb-4">{{ project.description }}</p>
              <div class="flex flex-wrap gap-2 mb-4">
                <span 
                  v-for="tech in project.technologies" 
                  :key="tech" 
                  class="bg-gray-100 dark:bg-gray-700 text-gray-800 dark:text-gray-200 text-xs px-3 py-1 rounded-full"
                >
                  {{ tech }}
                </span>
              </div>
              <div class="flex justify-between items-center">
                <span class="text-sm text-gray-500 dark:text-gray-400">{{ project.date }}</span>
                <div class="flex items-center text-blue-600 dark:text-blue-400 font-medium">
                  查看详情
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                    <path fill-rule="evenodd" d="M10.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L12.586 11H5a1 1 0 110-2h7.586l-2.293-2.293a1 1 0 010-1.414z" clip-rule="evenodd" />
                  </svg>
                </div>
              </div>
            </div>
          </NuxtLink>
        </div>
      </div>
      
      <!-- No Results -->
      <div v-if="filteredProjects.length === 0" class="text-center py-12">
        <p class="text-gray-600 dark:text-gray-400 text-lg">没有找到符合条件的项目</p>
        <button @click="selectedCategory = ''" class="mt-4 text-blue-600 dark:text-blue-400 font-medium">
          查看所有项目
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

// Fetch all projects
const { data: projects } = await useAsyncData('projects', () => 
  queryContent('projects')
    .sort({ date: -1 })
    .find()
);

// Filter by category
const selectedCategory = ref('');

// Get all unique categories
const categories = computed(() => {
  const cats = new Set();
  projects.value.forEach(project => {
    if (project.category) {
      cats.add(project.category);
    }
  });
  return Array.from(cats);
});

// Filter projects based on selected category
const filteredProjects = computed(() => {
  if (!selectedCategory.value) {
    return projects.value;
  }
  
  return projects.value.filter(project => 
    project.category === selectedCategory.value
  );
});

// Set page meta
useHead({
  title: '作品集',
  meta: [
    { name: 'description', content: '我的技术项目作品集，展示我的开发技能和项目经验' }
  ]
});
</script>
