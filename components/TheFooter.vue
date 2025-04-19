<template>
  <footer class="bg-gray-100 dark:bg-gray-900 py-8">
    <div class="container mx-auto px-4">
      <div class="flex flex-col md:flex-row justify-between items-center">
        <div class="mb-4 md:mb-0">
          <p class="text-gray-600 dark:text-gray-400">© {{ new Date().getFullYear() }} 个人技术博客与作品集</p>
        </div>
        <div class="flex space-x-4">
          <a href="https://github.com/" target="_blank" rel="noopener noreferrer" class="text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white">
            GitHub
          </a>
          <a href="https://twitter.com/" target="_blank" rel="noopener noreferrer" class="text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white">
            Twitter
          </a>
          <a href="https://linkedin.com/" target="_blank" rel="noopener noreferrer" class="text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white">
            LinkedIn
          </a>
        </div>
      </div>
    </div>
  </footer>
</template>
