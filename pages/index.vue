<template>
  <div>
    <!-- Hero Section -->
    <section class="py-12 md:py-20 bg-gradient-to-r from-blue-500 to-purple-600 text-white">
      <div class="container mx-auto px-4">
        <div class="max-w-3xl mx-auto text-center">
          <h1 class="text-4xl md:text-6xl font-bold mb-6 whitespace-nowrap">欢迎来到我的技术博客与作品集</h1>
          <p class="text-xl md:text-2xl mb-8">分享我的技术见解、项目经验和学习心得</p>
          <div class="flex flex-col sm:flex-row justify-center gap-4">
            <NuxtLink to="/blog" class="bg-white text-blue-600 hover:bg-gray-100 px-6 py-3 rounded-lg font-medium transition">
              阅读博客
            </NuxtLink>
            <NuxtLink to="/projects" class="bg-transparent border-2 border-white hover:bg-white hover:text-blue-600 px-6 py-3 rounded-lg font-medium transition">
              查看作品集
            </NuxtLink>
          </div>
        </div>
      </div>
    </section>

    <!-- Latest Blog Posts -->
    <section class="py-12 bg-white dark:bg-gray-800">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold mb-8 text-center text-gray-800 dark:text-white">最新博客文章</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="post in latestPosts" :key="post._path" class="bg-gray-50 dark:bg-gray-700 rounded-lg overflow-hidden shadow-md transition hover:shadow-lg">
            <NuxtLink :to="post._path">
              <img v-if="post.image" :src="post.image" :alt="post.title" class="w-full h-48 object-cover">
              <div class="p-6">
                <div class="text-sm text-gray-500 dark:text-gray-400 mb-2">{{ formatDate(post.date) }}</div>
                <h3 class="text-xl font-semibold mb-2 text-gray-800 dark:text-white">{{ post.title }}</h3>
                <p class="text-gray-600 dark:text-gray-300 mb-4">{{ post.description }}</p>
                <div class="flex flex-wrap gap-2">
                  <span v-for="tag in post.tags" :key="tag" class="bg-blue-100 dark:bg-blue-900 text-blue-800 dark:text-blue-100 text-xs px-3 py-1 rounded-full">
                    {{ tag }}
                  </span>
                </div>
              </div>
            </NuxtLink>
          </div>
        </div>
        <div class="text-center mt-8">
          <NuxtLink to="/blog" class="inline-block bg-blue-600 hover:bg-blue-700 text-white px-6 py-3 rounded-lg font-medium transition">
            查看所有文章
          </NuxtLink>
        </div>
      </div>
    </section>

    <!-- Featured Projects -->
    <section class="py-12 bg-gray-50 dark:bg-gray-900">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold mb-8 text-center text-gray-800 dark:text-white">精选项目</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
          <div v-for="project in featuredProjects" :key="project._path" class="bg-white dark:bg-gray-800 rounded-lg overflow-hidden shadow-md transition hover:shadow-lg">
            <NuxtLink :to="project._path">
              <img v-if="project.image" :src="project.image" :alt="project.title" class="w-full h-64 object-cover">
              <div class="p-6">
                <h3 class="text-xl font-semibold mb-2 text-gray-800 dark:text-white">{{ project.title }}</h3>
                <p class="text-gray-600 dark:text-gray-300 mb-4">{{ project.description }}</p>
                <div class="flex flex-wrap gap-2 mb-4">
                  <span v-for="tech in project.technologies" :key="tech" class="bg-gray-100 dark:bg-gray-700 text-gray-800 dark:text-gray-200 text-xs px-3 py-1 rounded-full">
                    {{ tech }}
                  </span>
                </div>
                <div class="flex items-center text-blue-600 dark:text-blue-400 font-medium">
                  了解更多
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                    <path fill-rule="evenodd" d="M10.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L12.586 11H5a1 1 0 110-2h7.586l-2.293-2.293a1 1 0 010-1.414z" clip-rule="evenodd" />
                  </svg>
                </div>
              </div>
            </NuxtLink>
          </div>
        </div>
        <div class="text-center mt-8">
          <NuxtLink to="/projects" class="inline-block bg-blue-600 hover:bg-blue-700 text-white px-6 py-3 rounded-lg font-medium transition">
            查看所有项目
          </NuxtLink>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { formatDate } from '~/utils/date';

// Fetch latest blog posts
const { data: latestPosts } = await useAsyncData('latestPosts', () => 
  queryContent('blog')
    .sort({ date: -1 })
    .limit(3)
    .find()
);

// Fetch featured projects
const { data: featuredProjects } = await useAsyncData('featuredProjects', () => 
  queryContent('projects')
    .where({ featured: true })
    .limit(2)
    .find()
);
</script>
