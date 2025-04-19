<template>
  <div class="max-w-4xl mx-auto">
    <h1 class="text-3xl md:text-4xl font-bold mb-8 text-black dark:text-black">关于我</h1>
    
    <!-- Profile Section -->
    <div class="bg-white dark:bg-gray-800 rounded-lg shadow-md p-6 md:p-8 mb-8">
      <div class="md:flex items-start">
        <div class="md:w-1/3 mb-6 md:mb-0 md:mr-8">
          <img src="/images/profile.svg" alt="Profile" class="w-full rounded-lg">
        </div>
        <div class="md:w-2/3">
          <h2 class="text-2xl font-bold mb-4 text-gray-800 dark:text-white">个人简介</h2>
          <p class="text-gray-600 dark:text-gray-300 mb-4">
            你好！我是一名热爱技术的开发者，专注于Web开发和前端技术。我喜欢探索新技术，解决复杂问题，并创建用户友好的应用程序。
          </p>
          <p class="text-gray-600 dark:text-gray-300 mb-4">
            通过这个博客，我希望能够分享我的技术见解、项目经验和学习心得，同时展示我的作品集。我相信技术应该是开放和共享的，希望我的内容能够帮助到其他开发者。
          </p>
          <div class="flex space-x-4 mt-6">
            <a href="https://github.com/" target="_blank" rel="noopener noreferrer" class="text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white">
              <span class="sr-only">GitHub</span>
              <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                <path fill-rule="evenodd" d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z" clip-rule="evenodd" />
              </svg>
            </a>
            <a href="https://twitter.com/" target="_blank" rel="noopener noreferrer" class="text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white">
              <span class="sr-only">Twitter</span>
              <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                <path d="M8.29 20.251c7.547 0 11.675-6.253 11.675-11.675 0-.178 0-.355-.012-.53A8.348 8.348 0 0022 5.92a8.19 8.19 0 01-2.357.646 4.118 4.118 0 001.804-2.27 8.224 8.224 0 01-2.605.996 4.107 4.107 0 00-6.993 3.743 11.65 11.65 0 01-8.457-4.287 4.106 4.106 0 001.27 5.477A4.072 4.072 0 012.8 9.713v.052a4.105 4.105 0 003.292 4.022 4.095 4.095 0 01-1.853.07 4.108 4.108 0 003.834 2.85A8.233 8.233 0 012 18.407a11.616 11.616 0 006.29 1.84" />
              </svg>
            </a>
            <a href="https://linkedin.com/" target="_blank" rel="noopener noreferrer" class="text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white">
              <span class="sr-only">LinkedIn</span>
              <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                <path fill-rule="evenodd" d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z" clip-rule="evenodd" />
              </svg>
            </a>
          </div>
        </div>
      </div>
    </div>
    
    <!-- Skills Section -->
    <div class="bg-white dark:bg-gray-800 rounded-lg shadow-md p-6 md:p-8 mb-8">
      <h2 class="text-2xl font-bold mb-6 text-gray-800 dark:text-white">技能</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div>
          <h3 class="text-xl font-semibold mb-4 text-gray-800 dark:text-white">前端开发</h3>
          <ul class="space-y-2">
            <li class="flex items-center">
              <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2.5">
                <div class="bg-blue-600 h-2.5 rounded-full" style="width: 95%"></div>
              </div>
              <span class="ml-4 text-gray-600 dark:text-gray-300 w-24">HTML/CSS</span>
            </li>
            <li class="flex items-center">
              <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2.5">
                <div class="bg-blue-600 h-2.5 rounded-full" style="width: 90%"></div>
              </div>
              <span class="ml-4 text-gray-600 dark:text-gray-300 w-24">JavaScript</span>
            </li>
            <li class="flex items-center">
              <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2.5">
                <div class="bg-blue-600 h-2.5 rounded-full" style="width: 85%"></div>
              </div>
              <span class="ml-4 text-gray-600 dark:text-gray-300 w-24">Vue.js</span>
            </li>
            <li class="flex items-center">
              <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2.5">
                <div class="bg-blue-600 h-2.5 rounded-full" style="width: 80%"></div>
              </div>
              <span class="ml-4 text-gray-600 dark:text-gray-300 w-24">React</span>
            </li>
          </ul>
        </div>
        <div>
          <h3 class="text-xl font-semibold mb-4 text-gray-800 dark:text-white">后端开发</h3>
          <ul class="space-y-2">
            <li class="flex items-center">
              <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2.5">
                <div class="bg-blue-600 h-2.5 rounded-full" style="width: 85%"></div>
              </div>
              <span class="ml-4 text-gray-600 dark:text-gray-300 w-24">Node.js</span>
            </li>
            <li class="flex items-center">
              <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2.5">
                <div class="bg-blue-600 h-2.5 rounded-full" style="width: 75%"></div>
              </div>
              <span class="ml-4 text-gray-600 dark:text-gray-300 w-24">Express</span>
            </li>
            <li class="flex items-center">
              <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2.5">
                <div class="bg-blue-600 h-2.5 rounded-full" style="width: 70%"></div>
              </div>
              <span class="ml-4 text-gray-600 dark:text-gray-300 w-24">MongoDB</span>
            </li>
            <li class="flex items-center">
              <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2.5">
                <div class="bg-blue-600 h-2.5 rounded-full" style="width: 65%"></div>
              </div>
              <span class="ml-4 text-gray-600 dark:text-gray-300 w-24">SQL</span>
            </li>
          </ul>
        </div>
      </div>
    </div>
    
    <!-- Experience Section -->
    <div class="bg-white dark:bg-gray-800 rounded-lg shadow-md p-6 md:p-8 mb-8">
      <h2 class="text-2xl font-bold mb-6 text-gray-800 dark:text-white">经验</h2>
      <div class="space-y-6">
        <div class="border-l-4 border-blue-600 pl-4">
          <h3 class="text-xl font-semibold mb-1 text-gray-800 dark:text-white">高级前端开发工程师</h3>
          <p class="text-gray-500 dark:text-gray-400 mb-2">某科技公司 | 2020 - 至今</p>
          <p class="text-gray-600 dark:text-gray-300">
            负责公司核心产品的前端开发，使用Vue.js和Nuxt.js构建高性能、响应式的Web应用程序。优化前端性能，提升用户体验，并与后端团队协作实现功能需求。
          </p>
        </div>
        <div class="border-l-4 border-blue-600 pl-4">
          <h3 class="text-xl font-semibold mb-1 text-gray-800 dark:text-white">Web开发工程师</h3>
          <p class="text-gray-500 dark:text-gray-400 mb-2">某互联网公司 | 2018 - 2020</p>
          <p class="text-gray-600 dark:text-gray-300">
            参与多个Web项目的开发，负责前端界面实现和后端API对接。使用React和Node.js构建现代化Web应用，并参与代码审查和技术分享。
          </p>
        </div>
      </div>
    </div>
    
    <!-- Contact Section -->
    <div class="bg-white dark:bg-gray-800 rounded-lg shadow-md p-6 md:p-8">
      <h2 class="text-2xl font-bold mb-6 text-gray-800 dark:text-white">联系我</h2>
      <p class="text-gray-600 dark:text-gray-300 mb-6">
        如果你有任何问题、合作机会或者只是想打个招呼，欢迎通过以下方式联系我：
      </p>
      <div class="space-y-4">
        <div class="flex items-center">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-blue-600 dark:text-blue-400 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
          </svg>
          <span class="text-gray-600 dark:text-gray-300">email@example.com</span>
        </div>
        <div class="flex items-center">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-blue-600 dark:text-blue-400 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
          </svg>
          <span class="text-gray-600 dark:text-gray-300">中国，北京</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// Set page meta
useHead({
  title: '关于我',
  meta: [
    { name: 'description', content: '了解更多关于我的信息，包括我的技能、经验和联系方式' }
  ]
});
</script>
