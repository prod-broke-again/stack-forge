<template>
  <div class="h-screen bg-gray-900 flex flex-col">
    <!-- Compact Header - LARAGON Style -->
    <div class="bg-slate-800 border-b border-gray-700 flex items-center justify-between px-4 py-3">
      <!-- Left Section - Logo & Status -->
      <div class="flex items-center space-x-4">
        <!-- Logo -->
        <div class="flex items-center space-x-2">
          <div class="w-8 h-8 bg-cyan-600 rounded-lg flex items-center justify-center">
            <ServerIcon class="w-5 h-5 text-white" />
          </div>
          <span class="text-white font-semibold text-lg">Stack Forge</span>
        </div>
      </div>

      <!-- Right Section - Quick Actions & Controls -->
      <div class="flex items-center space-x-2">
        <!-- Navigation -->
        <nav class="flex items-center space-x-1 mr-4">
          <router-link
            to="/"
            class="flex items-center space-x-2 px-3 py-1.5 rounded-md text-sm font-medium transition-colors"
            :class="
              $route.path === '/'
                ? 'bg-cyan-600 text-white'
                : 'text-gray-300 hover:bg-slate-600 hover:text-white'
            "
          >
            <HomeIcon class="w-4 h-4" />
            <span>Главная</span>
          </router-link>
          <router-link
            to="/settings"
            class="flex items-center space-x-2 px-3 py-1.5 rounded-md text-sm font-medium transition-colors"
            :class="
              $route.path === '/settings'
                ? 'bg-cyan-600 text-white'
                : 'text-gray-300 hover:bg-slate-600 hover:text-white'
            "
          >
            <CogIcon class="w-4 h-4" />
            <span>Настройки</span>
          </router-link>
        </nav>

        <!-- Global Service Controls -->
        <div class="flex items-center space-x-1 border-l border-gray-600 pl-4">
          <button
            @click="startAllServices"
            class="p-2 text-green-400 hover:bg-green-400/20 rounded-md transition-colors"
            title="Запустить все сервисы"
            :disabled="allServicesRunning"
          >
            <PlayIcon class="w-4 h-4" />
          </button>
          <button
            @click="stopAllServices"
            class="p-2 text-red-400 hover:bg-red-400/20 rounded-md transition-colors"
            title="Остановить все сервисы"
            :disabled="!anyServiceRunning"
          >
            <StopIcon class="w-4 h-4" />
          </button>
        </div>

        <!-- Window Controls -->
        <div class="flex items-center space-x-1 border-l border-gray-600 pl-4">
          <button
            class="w-8 h-8 flex items-center justify-center hover:bg-slate-600 rounded-md transition-colors"
            title="Свернуть"
          >
            <MinusIcon class="w-4 h-4 text-gray-400" />
          </button>
          <button
            class="w-8 h-8 flex items-center justify-center hover:bg-slate-600 rounded-md transition-colors"
            title="Развернуть"
          >
            <ArrowsPointingOutIcon class="w-4 h-4 text-gray-400" />
          </button>
          <button
            class="w-8 h-8 flex items-center justify-center hover:bg-red-600 rounded-md transition-colors"
            title="Закрыть"
          >
            <XMarkIcon class="w-4 h-4 text-gray-400" />
          </button>
        </div>
      </div>
    </div>

    <!-- Main Content Area -->
    <div class="flex-1 flex">
      <!-- Main Content -->
      <div class="flex-1 flex flex-col min-h-0">
        <div class="flex-1 overflow-auto bg-gray-900">
          <router-view />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import {
  HomeIcon,
  CogIcon,
  ServerIcon,
  MinusIcon,
  ArrowsPointingOutIcon,
  XMarkIcon,
  PlayIcon,
  StopIcon
} from '@heroicons/vue/24/outline'

// Простое состояние сервисов (только для глобальных операций)
const services = ref({
  php: { running: false, loading: false },
  nodejs: { running: false, loading: false },
  nginx: { running: false, loading: false },
  mysql: { running: false, loading: false },
  redis: { running: false, loading: false },
  docker: { running: false, loading: false }
})

// Функции управления сервисами (используются только для глобальных операций)
const startAllServices = async (): Promise<void> => {
  const promises = Object.keys(services.value).map(async (serviceName) => {
    const service = services.value[serviceName as keyof typeof services.value]
    if (!service.running) {
      service.loading = true
      await new Promise((resolve) => setTimeout(resolve, 800))
      service.running = true
      service.loading = false
    }
  })

  await Promise.all(promises)
}

const stopAllServices = async (): Promise<void> => {
  const promises = Object.keys(services.value).map(async (serviceName) => {
    const service = services.value[serviceName as keyof typeof services.value]
    if (service.running) {
      service.loading = true
      await new Promise((resolve) => setTimeout(resolve, 800))
      service.running = false
      service.loading = false
    }
  })

  await Promise.all(promises)
}
</script>
