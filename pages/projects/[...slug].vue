<template>
  <div class="max-w-4xl mx-auto">
    <div v-if="project">
      <!-- Project Header -->
      <div class="mb-8">
        <h1 class="text-3xl md:text-4xl font-bold mb-4 text-black dark:text-black">{{ project.title }}</h1>
        <div class="flex items-center text-sm text-gray-500 dark:text-gray-400 mb-4">
          <span>{{ project.date }}</span>
          <span v-if="project.category" class="mx-2">•</span>
          <span v-if="project.category">{{ project.category }}</span>
        </div>
        <img v-if="project.image" :src="project.image" :alt="project.title" class="w-full h-64 md:h-96 object-cover rounded-lg mb-6">
      </div>
      
      <!-- Project Links -->
      <div v-if="project.links" class="flex flex-wrap gap-4 mb-8">
        <a 
          v-for="(link, key) in project.links" 
          :key="key" 
          :href="link" 
          target="_blank" 
          rel="noopener noreferrer"
          class="inline-flex items-center px-4 py-2 bg-gray-100 dark:bg-gray-700 text-gray-800 dark:text-gray-200 rounded-lg hover:bg-gray-200 dark:hover:bg-gray-600 transition"
        >
          <span v-if="key === 'github'">GitHub</span>
          <span v-else-if="key === 'demo'">在线演示</span>
          <span v-else-if="key === 'website'">网站</span>
          <span v-else>{{ key }}</span>
          <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 ml-1" viewBox="0 0 20 20" fill="currentColor">
            <path d="M11 3a1 1 0 100 2h2.586l-6.293 6.293a1 1 0 101.414 1.414L15 6.414V9a1 1 0 102 0V4a1 1 0 00-1-1h-5z" />
            <path d="M5 5a2 2 0 00-2 2v8a2 2 0 002 2h8a2 2 0 002-2v-3a1 1 0 10-2 0v3H5V7h3a1 1 0 000-2H5z" />
          </svg>
        </a>
      </div>
      
      <!-- Technologies Used -->
      <div v-if="project.technologies && project.technologies.length > 0" class="mb-8">
        <h2 class="text-xl font-semibold mb-3 text-gray-800 dark:text-white">使用技术</h2>
        <div class="flex flex-wrap gap-2">
          <span 
            v-for="tech in project.technologies" 
            :key="tech" 
            class="bg-gray-100 dark:bg-gray-700 text-gray-800 dark:text-gray-200 px-3 py-1 rounded-full"
          >
            {{ tech }}
          </span>
        </div>
      </div>
      
      <!-- Project Content -->
      <div class="prose prose-lg dark:prose-invert max-w-none">
        <ContentRenderer :value="project" />
      </div>
      
      <!-- Other Projects -->
      <div v-if="otherProjects.length > 0" class="mt-12 pt-8 border-t border-gray-200 dark:border-gray-700">
        <h2 class="text-2xl font-bold mb-6 text-gray-800 dark:text-white">其他项目</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <div 
            v-for="otherProject in otherProjects" 
            :key="otherProject._path" 
            class="bg-white dark:bg-gray-800 rounded-lg overflow-hidden shadow"
          >
            <NuxtLink :to="otherProject._path" class="block hover:opacity-90 transition">
              <div class="p-4">
                <h3 class="text-lg font-semibold mb-2 text-gray-800 dark:text-white">{{ otherProject.title }}</h3>
                <p class="text-gray-600 dark:text-gray-300 line-clamp-2">{{ otherProject.description }}</p>
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
// Get the current route
const route = useRoute();

// Fetch the current project
const { data: project } = await useAsyncData(`project-${route.params.slug.join('/')}`, () => 
  queryContent('projects', ...route.params.slug).findOne()
);

// Fetch other projects
const { data: otherProjects } = await useAsyncData(`other-projects-${route.params.slug.join('/')}`, async () => {
  if (!project.value) {
    return [];
  }
  
  // Find other projects, excluding the current one
  const others = await queryContent('projects')
    .where({ _path: { $ne: project.value._path } })
    .limit(2)
    .find();
    
  return others;
});

// Set page meta
useHead(() => ({
  title: project.value?.title,
  meta: [
    { name: 'description', content: project.value?.description }
  ]
}));
</script>
