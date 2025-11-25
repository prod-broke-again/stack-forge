<template>
  <div class="p-6 space-y-6">
    <!-- Settings Header -->
    <div class="bg-slate-800 border border-gray-700 rounded-xl p-6">
      <h1 class="text-xl font-semibold text-white mb-2">Настройки</h1>
      <p class="text-gray-400">Настройка среды разработки</p>
    </div>

    <!-- Settings Sections -->
    <div class="grid grid-cols-2 gap-6">
      <!-- General Settings -->
      <div class="bg-slate-800 border border-gray-700 rounded-xl">
        <div class="px-6 py-4 border-b border-gray-700">
          <h2 class="text-lg font-semibold text-white flex items-center space-x-2">
            <CogIcon class="w-5 h-5 text-gray-400" />
            <span>Общие</span>
          </h2>
        </div>
        <div class="p-6 space-y-6">
          <div>
            <label class="block text-sm font-medium text-gray-300 mb-2"
              >Диапазон портов по умолчанию</label
            >
            <div class="flex space-x-3">
              <input
                type="number"
                value="8000"
                class="flex-1 px-3 py-2 text-sm bg-slate-600 border border-gray-600 text-white rounded-lg focus:ring-2 focus:ring-cyan-500 focus:border-cyan-500"
              />
              <span class="flex items-center text-sm text-gray-400">до</span>
              <input
                type="number"
                value="8100"
                class="flex-1 px-3 py-2 text-sm bg-slate-600 border border-gray-600 text-white rounded-lg focus:ring-2 focus:ring-cyan-500 focus:border-cyan-500"
              />
            </div>
          </div>

          <div>
            <label class="block text-sm font-medium text-gray-300 mb-2">Автозапуск сервисов</label>
            <div class="flex items-center space-x-3">
              <input
                type="checkbox"
                class="w-4 h-4 text-cyan-600 bg-slate-600 border-gray-600 rounded focus:ring-cyan-500"
                checked
              />
              <span class="text-sm text-gray-300"
                >Запускать сервисы автоматически при запуске приложения</span
              >
            </div>
          </div>

          <div>
            <label class="block text-sm font-medium text-gray-300 mb-2">Тема</label>
            <select
              class="w-full px-3 py-2 text-sm bg-slate-600 border border-gray-600 text-white rounded-lg focus:ring-2 focus:ring-cyan-500 focus:border-cyan-500"
            >
              <option>Светлая</option>
              <option selected>Темная</option>
              <option>Авто</option>
            </select>
          </div>
        </div>
      </div>

      <!-- Service Settings -->
      <div class="bg-slate-800 border border-gray-700 rounded-xl">
        <div class="px-6 py-4 border-b border-gray-700">
          <h2 class="text-lg font-semibold text-white flex items-center space-x-2">
            <ServerIcon class="w-5 h-5 text-gray-400" />
            <span>Сервисы</span>
          </h2>
        </div>
        <div class="p-6 space-y-6">
          <div>
            <label class="block text-sm font-medium text-gray-300 mb-2">Версия PHP</label>
            <select
              class="w-full px-3 py-2 text-sm bg-slate-600 border border-gray-600 text-white rounded-lg focus:ring-2 focus:ring-cyan-500 focus:border-cyan-500"
            >
              <option selected>8.2.0</option>
              <option>8.1.0</option>
              <option>8.0.0</option>
            </select>
          </div>

          <div>
            <label class="block text-sm font-medium text-gray-300 mb-2">Версия Node.js</label>
            <select
              class="w-full px-3 py-2 text-sm bg-slate-600 border border-gray-600 text-white rounded-lg focus:ring-2 focus:ring-cyan-500 focus:border-cyan-500"
            >
              <option selected>18.17.0</option>
              <option>16.20.0</option>
              <option>14.21.0</option>
            </select>
          </div>

          <div>
            <label class="block text-sm font-medium text-gray-300 mb-2">Веб-сервер</label>
            <div class="space-y-2">
              <div class="flex items-center space-x-3">
                <input
                  type="radio"
                  name="webserver"
                  value="nginx"
                  class="w-4 h-4 text-cyan-600 bg-slate-600 border-gray-600 focus:ring-cyan-500"
                  checked
                />
                <span class="text-sm text-gray-300">Nginx</span>
              </div>
              <div class="flex items-center space-x-3">
                <input
                  type="radio"
                  name="webserver"
                  value="apache"
                  class="w-4 h-4 text-cyan-600 bg-slate-600 border-gray-600 focus:ring-cyan-500"
                />
                <span class="text-sm text-gray-300">Apache</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- SSL Settings -->
      <div class="bg-slate-800 border border-gray-700 rounded-xl">
        <div class="px-6 py-4 border-b border-gray-700">
          <h2 class="text-lg font-semibold text-white flex items-center space-x-2">
            <ShieldCheckIcon class="w-5 h-5 text-gray-400" />
            <span>SSL сертификат</span>
          </h2>
        </div>
        <div class="p-6 space-y-6">
          <div>
            <label class="block text-sm font-medium text-gray-300 mb-2">Домен</label>
            <input
              type="text"
              value=".test"
              class="w-full px-3 py-2 text-sm bg-slate-600 border border-gray-600 text-white rounded-lg focus:ring-2 focus:ring-cyan-500 focus:border-cyan-500"
            />
          </div>

          <div>
            <label class="block text-sm font-medium text-gray-300 mb-2">Статус сертификата</label>
            <div class="flex items-center space-x-3">
              <div class="w-2 h-2 bg-green-400 rounded-full"></div>
              <span class="text-sm text-green-400">Действителен до 2025-12-31</span>
            </div>
          </div>

          <button
            class="w-full px-4 py-2 text-sm bg-cyan-600 text-white hover:bg-cyan-700 rounded-lg transition-colors"
          >
            Перегенерировать сертификат
          </button>
        </div>
      </div>

      <!-- Database Settings -->
      <div class="bg-slate-800 border border-gray-700 rounded-xl">
        <div class="px-6 py-4 border-b border-gray-700">
          <h2 class="text-lg font-semibold text-white flex items-center space-x-2">
            <CircleStackIcon class="w-5 h-5 text-gray-400" />
            <span>База данных</span>
          </h2>
        </div>
        <div class="p-6 space-y-6">
          <div>
            <label class="block text-sm font-medium text-gray-300 mb-2">Порт MySQL</label>
            <input
              type="number"
              value="3306"
              class="w-full px-3 py-2 text-sm bg-slate-600 border border-gray-600 text-white rounded-lg focus:ring-2 focus:ring-cyan-500 focus:border-cyan-500"
            />
          </div>

          <div>
            <label class="block text-sm font-medium text-gray-300 mb-2">Порт PostgreSQL</label>
            <input
              type="number"
              value="5432"
              class="w-full px-3 py-2 text-sm bg-slate-600 border border-gray-600 text-white rounded-lg focus:ring-2 focus:ring-cyan-500 focus:border-cyan-500"
            />
          </div>

          <div>
            <label class="block text-sm font-medium text-gray-300 mb-2">Порт Redis</label>
            <input
              type="number"
              value="6379"
              class="w-full px-3 py-2 text-sm bg-slate-600 border border-gray-600 text-white rounded-lg focus:ring-2 focus:ring-cyan-500 focus:border-cyan-500"
            />
          </div>
        </div>
      </div>
    </div>

    <!-- Save Button -->
    <div class="flex justify-end">
      <button
        class="px-6 py-3 text-sm bg-cyan-600 text-white hover:bg-cyan-700 rounded-lg transition-colors font-medium"
      >
        Сохранить настройки
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { CogIcon, ServerIcon, ShieldCheckIcon, CircleStackIcon } from '@heroicons/vue/24/outline'
</script>
