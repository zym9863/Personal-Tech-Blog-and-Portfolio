<template>
  <div class="max-w-3xl mx-auto">
    <div v-if="post">
      <!-- Post Header -->
      <div class="mb-8">
        <div class="flex items-center text-sm text-gray-500 dark:text-gray-400 mb-2">
          <span>{{ formatDate(post.date) }}</span>
          <span class="mx-2">•</span>
          <span>{{ post.readingTime || '5 分钟阅读' }}</span>
        </div>
        <h1 class="text-3xl md:text-4xl font-bold mb-4 text-black dark:text-black">{{ post.title }}</h1>
        <div class="flex flex-wrap gap-2 mb-6">
          <span v-for="tag in post.tags" :key="tag" class="bg-blue-100 dark:bg-blue-900 text-blue-800 dark:text-blue-100 text-xs px-3 py-1 rounded-full">
            {{ tag }}
          </span>
        </div>
        <img v-if="post.image" :src="post.image" :alt="post.title" class="w-full h-64 md:h-96 object-cover rounded-lg mb-6">
      </div>
      
      <!-- Post Content -->
      <div class="prose prose-lg dark:prose-invert max-w-none">
        <ContentRenderer :value="post" />
      </div>
      
      <!-- Author Info -->
      <div class="mt-12 pt-8 border-t border-gray-200 dark:border-gray-700">
        <div class="flex items-center">
          <img src="/images/avatar.jpg" alt="Author" class="w-16 h-16 rounded-full mr-4" onerror="this.src='https://via.placeholder.com/64'">
          <div>
            <h3 class="text-lg font-semibold text-gray-800 dark:text-white">作者</h3>
            <p class="text-gray-600 dark:text-gray-300">技术博主，分享前端开发、Web技术和软件工程的见解与经验。</p>
          </div>
        </div>
      </div>
      
      <!-- Related Posts -->
      <div v-if="relatedPosts.length > 0" class="mt-12">
        <h2 class="text-2xl font-bold mb-6 text-gray-800 dark:text-white">相关文章</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <div v-for="relatedPost in relatedPosts" :key="relatedPost._path" class="bg-white dark:bg-gray-800 rounded-lg overflow-hidden shadow">
            <NuxtLink :to="relatedPost._path" class="block hover:opacity-90 transition">
              <div class="p-4">
                <h3 class="text-lg font-semibold mb-2 text-gray-800 dark:text-white">{{ relatedPost.title }}</h3>
                <div class="text-sm text-gray-500 dark:text-gray-400">{{ formatDate(relatedPost.date) }}</div>
              </div>
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>
    
    <!-- Loading State -->
    <div v-else class="py-12 text-center">
      <p class="text-gray-600 dark:text-gray-400">加载中...</p>
    </div>
  </div>
</template>

<script setup>
import { formatDate } from '~/utils/date';

// Get the current route
const route = useRoute();

// Fetch the current post
const { data: post } = await useAsyncData(`post-${route.params.slug.join('/')}`, () => 
  queryContent('blog', ...route.params.slug).findOne()
);

// Fetch related posts (posts with similar tags)
const { data: relatedPosts } = await useAsyncData(`related-posts-${route.params.slug.join('/')}`, async () => {
  if (!post.value || !post.value.tags || post.value.tags.length === 0) {
    return [];
  }
  
  // Find posts with at least one matching tag
  const related = await queryContent('blog')
    .where({ 
      _path: { $ne: post.value._path },
      tags: { $contains: post.value.tags[0] }
    })
    .limit(2)
    .find();
    
  return related;
});

// Set page meta
useHead(() => ({
  title: post.value?.title,
  meta: [
    { name: 'description', content: post.value?.description }
  ]
}));
</script>
