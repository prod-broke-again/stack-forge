<template>
  <div class="p-6 space-y-6">
    <!-- Service Control Panel - LARAGON Style -->
    <div class="grid grid-cols-3 md:grid-cols-6 gap-3">
      <!-- PHP Service -->
      <div
        class="bg-slate-800 border border-gray-700 rounded-lg p-3 hover:bg-slate-700 transition-colors"
      >
        <div class="flex flex-col items-center space-y-2">
          <div class="relative">
            <div class="w-10 h-10 bg-violet-600 rounded-full flex items-center justify-center">
              <CodeBracketIcon class="w-5 h-5 text-white" />
            </div>
            <div
              class="absolute -top-1 -right-1 w-3 h-3 rounded-full border-2 border-gray-800 flex items-center justify-center"
              :class="services.php.running ? 'bg-green-400' : 'bg-gray-600'"
            >
              <div
                v-if="services.php.loading"
                class="w-1 h-1 border border-white border-t-transparent rounded-full animate-spin"
              ></div>
            </div>
          </div>
          <div class="text-center">
            <h3 class="text-white font-semibold text-xs">PHP</h3>
            <p class="text-gray-400 text-xs">{{ services.php.port }}</p>
          </div>
          <button
            @click="toggleService('php')"
            :disabled="services.php.loading"
            class="w-full py-1 px-2 rounded text-xs font-medium transition-colors"
            :class="
              services.php.running
                ? 'bg-pink-600 hover:bg-pink-700 text-white'
                : 'bg-green-600 hover:bg-green-700 text-white'
            "
          >
            {{ services.php.running ? '■' : '▶' }}
          </button>
        </div>
      </div>

      <!-- Node.js Service -->
      <div
        class="bg-slate-800 border border-gray-700 rounded-lg p-3 hover:bg-slate-700 transition-colors"
      >
        <div class="flex flex-col items-center space-y-2">
          <div class="relative">
            <div class="w-10 h-10 bg-emerald-600 rounded-full flex items-center justify-center">
              <CommandLineIcon class="w-5 h-5 text-white" />
            </div>
            <div
              class="absolute -top-1 -right-1 w-3 h-3 rounded-full border-2 border-gray-800 flex items-center justify-center"
              :class="services.nodejs.running ? 'bg-green-400' : 'bg-gray-600'"
            >
              <div
                v-if="services.nodejs.loading"
                class="w-1 h-1 border border-white border-t-transparent rounded-full animate-spin"
              ></div>
            </div>
          </div>
          <div class="text-center">
            <h3 class="text-white font-semibold text-xs">Node</h3>
            <p class="text-gray-400 text-xs">{{ services.nodejs.port }}</p>
          </div>
          <button
            @click="toggleService('nodejs')"
            :disabled="services.nodejs.loading"
            class="w-full py-1 px-2 rounded text-xs font-medium transition-colors"
            :class="
              services.nodejs.running
                ? 'bg-pink-600 hover:bg-pink-700 text-white'
                : 'bg-green-600 hover:bg-green-700 text-white'
            "
          >
            {{ services.nodejs.running ? '■' : '▶' }}
          </button>
        </div>
      </div>

      <!-- Nginx Service -->
      <div
        class="bg-slate-800 border border-gray-700 rounded-lg p-3 hover:bg-slate-700 transition-colors"
      >
        <div class="flex flex-col items-center space-y-2">
          <div class="relative">
            <div class="w-10 h-10 bg-pink-600 rounded-full flex items-center justify-center">
              <GlobeAltIcon class="w-5 h-5 text-white" />
            </div>
            <div
              class="absolute -top-1 -right-1 w-3 h-3 rounded-full border-2 border-gray-800 flex items-center justify-center"
              :class="services.nginx.running ? 'bg-green-400' : 'bg-gray-600'"
            >
              <div
                v-if="services.nginx.loading"
                class="w-1 h-1 border border-white border-t-transparent rounded-full animate-spin"
              ></div>
            </div>
          </div>
          <div class="text-center">
            <h3 class="text-white font-semibold text-xs">Nginx</h3>
            <p class="text-gray-400 text-xs">{{ services.nginx.port }}</p>
          </div>
          <button
            @click="toggleService('nginx')"
            :disabled="services.nginx.loading"
            class="w-full py-1 px-2 rounded text-xs font-medium transition-colors"
            :class="
              services.nginx.running
                ? 'bg-pink-600 hover:bg-pink-700 text-white'
                : 'bg-green-600 hover:bg-green-700 text-white'
            "
          >
            {{ services.nginx.running ? '■' : '▶' }}
          </button>
        </div>
      </div>

      <!-- MySQL Service -->
      <div
        class="bg-slate-800 border border-gray-700 rounded-lg p-3 hover:bg-slate-700 transition-colors"
      >
        <div class="flex flex-col items-center space-y-2">
          <div class="relative">
            <div class="w-10 h-10 bg-blue-600 rounded-full flex items-center justify-center">
              <ServerIcon class="w-5 h-5 text-white" />
            </div>
            <div
              class="absolute -top-1 -right-1 w-3 h-3 rounded-full border-2 border-gray-800 flex items-center justify-center"
              :class="services.mysql.running ? 'bg-green-400' : 'bg-gray-600'"
            >
              <div
                v-if="services.mysql.loading"
                class="w-1 h-1 border border-white border-t-transparent rounded-full animate-spin"
              ></div>
            </div>
          </div>
          <div class="text-center">
            <h3 class="text-white font-semibold text-xs">MySQL</h3>
            <p class="text-gray-400 text-xs">{{ services.mysql.port }}</p>
          </div>
          <button
            @click="toggleService('mysql')"
            :disabled="services.mysql.loading"
            class="w-full py-1 px-2 rounded text-xs font-medium transition-colors"
            :class="
              services.mysql.running
                ? 'bg-pink-600 hover:bg-pink-700 text-white'
                : 'bg-green-600 hover:bg-green-700 text-white'
            "
          >
            {{ services.mysql.running ? '■' : '▶' }}
          </button>
        </div>
      </div>

      <!-- Redis Service -->
      <div
        class="bg-slate-800 border border-gray-700 rounded-lg p-3 hover:bg-slate-700 transition-colors"
      >
        <div class="flex flex-col items-center space-y-2">
          <div class="relative">
            <div class="w-10 h-10 bg-yellow-600 rounded-full flex items-center justify-center">
              <CogIcon class="w-5 h-5 text-white" />
            </div>
            <div
              class="absolute -top-1 -right-1 w-3 h-3 rounded-full border-2 border-gray-800 flex items-center justify-center"
              :class="services.redis.running ? 'bg-green-400' : 'bg-gray-600'"
            >
              <div
                v-if="services.redis.loading"
                class="w-1 h-1 border border-white border-t-transparent rounded-full animate-spin"
              ></div>
            </div>
          </div>
          <div class="text-center">
            <h3 class="text-white font-semibold text-xs">Redis</h3>
            <p class="text-gray-400 text-xs">{{ services.redis.port }}</p>
          </div>
          <button
            @click="toggleService('redis')"
            :disabled="services.redis.loading"
            class="w-full py-1 px-2 rounded text-xs font-medium transition-colors"
            :class="
              services.redis.running
                ? 'bg-pink-600 hover:bg-pink-700 text-white'
                : 'bg-green-600 hover:bg-green-700 text-white'
            "
          >
            {{ services.redis.running ? '■' : '▶' }}
          </button>
        </div>
      </div>

      <!-- Docker Service -->
      <div
        class="bg-slate-800 border border-gray-700 rounded-lg p-3 hover:bg-slate-700 transition-colors"
      >
        <div class="flex flex-col items-center space-y-2">
          <div class="relative">
            <div class="w-10 h-10 bg-indigo-600 rounded-full flex items-center justify-center">
              <CommandLineIcon class="w-5 h-5 text-white" />
            </div>
            <div
              class="absolute -top-1 -right-1 w-3 h-3 rounded-full border-2 border-gray-800 flex items-center justify-center"
              :class="services.docker.running ? 'bg-green-400' : 'bg-gray-600'"
            >
              <div
                v-if="services.docker.loading"
                class="w-1 h-1 border border-white border-t-transparent rounded-full animate-spin"
              ></div>
            </div>
          </div>
          <div class="text-center">
            <h3 class="text-white font-semibold text-xs">Docker</h3>
            <p class="text-gray-400 text-xs">{{ services.docker.port }}</p>
          </div>
          <button
            @click="toggleService('docker')"
            :disabled="services.docker.loading"
            class="w-full py-1 px-2 rounded text-xs font-medium transition-colors"
            :class="
              services.docker.running
                ? 'bg-pink-600 hover:bg-pink-700 text-white'
                : 'bg-green-600 hover:bg-green-700 text-white'
            "
          >
            {{ services.docker.running ? '■' : '▶' }}
          </button>
        </div>
      </div>
    </div>

    <!-- Quick Actions Panel -->
    <div class="grid grid-cols-2 md:grid-cols-4 gap-3">
      <!-- Start All Services -->
      <button
        @click="startAllServices"
        :disabled="allServicesRunning"
        class="bg-slate-800 hover:bg-slate-700 border border-gray-700 rounded-lg p-4 transition-colors disabled:opacity-50"
      >
        <div class="flex flex-col items-center space-y-2">
          <div class="w-8 h-8 bg-green-600 rounded-full flex items-center justify-center">
            <PlayIcon class="w-4 h-4 text-white" />
          </div>
          <div class="text-center">
            <h3 class="text-white font-semibold text-sm">Всё</h3>
            <p class="text-gray-400 text-xs">Запуск</p>
          </div>
        </div>
      </button>

      <!-- Stop All Services -->
      <button
        @click="stopAllServices"
        :disabled="!anyServiceRunning"
        class="bg-slate-800 hover:bg-slate-700 border border-gray-700 rounded-lg p-4 transition-colors disabled:opacity-50"
      >
        <div class="flex flex-col items-center space-y-2">
          <div class="w-8 h-8 bg-pink-600 rounded-full flex items-center justify-center">
            <StopIcon class="w-4 h-4 text-white" />
          </div>
          <div class="text-center">
            <h3 class="text-white font-semibold text-sm">Всё</h3>
            <p class="text-gray-400 text-xs">Стоп</p>
          </div>
        </div>
      </button>

      <!-- Open Projects -->
      <button
        class="bg-slate-800 hover:bg-slate-700 border border-gray-700 rounded-lg p-4 transition-colors"
      >
        <div class="flex flex-col items-center space-y-2">
          <div class="w-8 h-8 bg-blue-600 rounded-full flex items-center justify-center">
            <FolderIcon class="w-4 h-4 text-white" />
          </div>
          <div class="text-center">
            <h3 class="text-white font-semibold text-sm">Проекты</h3>
            <p class="text-gray-400 text-xs">Папка</p>
          </div>
        </div>
      </button>

      <!-- Terminal -->
      <button
        class="bg-slate-800 hover:bg-slate-700 border border-gray-700 rounded-lg p-4 transition-colors"
      >
        <div class="flex flex-col items-center space-y-2">
          <div class="w-8 h-8 bg-purple-600 rounded-full flex items-center justify-center">
            <CommandLineIcon class="w-4 h-4 text-white" />
          </div>
          <div class="text-center">
            <h3 class="text-white font-semibold text-sm">Терминал</h3>
            <p class="text-gray-400 text-xs">CMD</p>
          </div>
        </div>
      </button>
    </div>

    <!-- System Information -->
    <div class="bg-slate-800 border border-gray-700 rounded-lg p-4">
      <h2 class="text-white font-semibold mb-3 flex items-center space-x-2">
        <ServerIcon class="w-4 h-4 text-blue-400" />
        <span class="text-sm">Информация о системе</span>
      </h2>
      <div class="grid grid-cols-2 gap-3">
        <div class="bg-slate-600 border border-gray-600 rounded-lg p-3">
          <div class="flex items-center justify-between mb-2">
            <span class="text-gray-300 text-xs">Процессор</span>
            <span class="text-emerald-400 text-xs font-medium">15%</span>
          </div>
          <div class="w-full bg-gray-600 rounded-full h-1.5">
            <div class="bg-emerald-500 h-1.5 rounded-full" style="width: 15%"></div>
          </div>
        </div>

        <div class="bg-slate-600 border border-gray-600 rounded-lg p-3">
          <div class="flex items-center justify-between mb-2">
            <span class="text-gray-300 text-xs">Память</span>
            <span class="text-blue-400 text-xs font-medium">2.1GB / 8GB</span>
          </div>
          <div class="w-full bg-gray-600 rounded-full h-1.5">
            <div class="bg-blue-500 h-1.5 rounded-full" style="width: 26%"></div>
          </div>
        </div>

        <div class="bg-slate-600 border border-gray-600 rounded-lg p-3">
          <div class="flex items-center justify-between mb-2">
            <span class="text-gray-300 text-xs">Диск</span>
            <span class="text-violet-400 text-xs font-medium">45GB / 500GB</span>
          </div>
          <div class="w-full bg-gray-600 rounded-full h-1.5">
            <div class="bg-violet-500 h-1.5 rounded-full" style="width: 9%"></div>
          </div>
        </div>

        <div class="bg-slate-600 border border-gray-600 rounded-lg p-3">
          <div class="flex items-center justify-between mb-2">
            <span class="text-gray-300 text-xs">Время работы</span>
            <span class="text-amber-400 text-xs font-medium">2h 34m</span>
          </div>
          <div class="w-full bg-gray-600 rounded-full h-1.5">
            <div class="bg-amber-500 h-1.5 rounded-full" style="width: 100%"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import {
  GlobeAltIcon,
  PlayIcon,
  StopIcon,
  CogIcon,
  ServerIcon,
  CommandLineIcon
} from '@heroicons/vue/24/outline'

// Простое состояние сервисов
const services = ref({
  php: {
    running: true,
    loading: false,
    port: 8000
  },
  nodejs: {
    running: false,
    loading: false,
    port: 3000
  },
  nginx: {
    running: true,
    loading: false,
    port: 80
  },
  mysql: {
    running: true,
    loading: false,
    port: 3306
  },
  redis: {
    running: false,
    loading: false,
    port: 6379
  },
  docker: {
    running: true,
    loading: false,
    port: 2376
  }
})

// Вычисляемые свойства
const allServicesRunning = computed(() => {
  return Object.values(services.value).every((service) => service.running)
})

const anyServiceRunning = computed(() => {
  return Object.values(services.value).some((service) => service.running)
})

// Простые функции управления сервисами
const toggleService = async (serviceName: keyof typeof services.value): Promise<void> => {
  const service = services.value[serviceName]
  service.loading = true

  // Имитация задержки
  await new Promise((resolve) => setTimeout(resolve, 1000))

  service.running = !service.running
  service.loading = false
}

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
