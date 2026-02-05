<template>
  <div class="p-6 h-full flex flex-col space-y-6">
    
    <div class="flex items-center justify-between bg-white/[0.03] border border-white/10 p-4 rounded-2xl backdrop-blur-sm">
      <div class="flex flex-col">
        <span class="text-xs font-black uppercase tracking-[0.2em] text-white/40">Global Controls</span>
        <span class="text-sm font-bold text-white">Всего сервисов: {{ Object.keys(services).length }}</span>
      </div>
      <div class="flex space-x-2">
        <button @click="stopAll" class="px-4 py-2 rounded-xl bg-rose-500/10 text-rose-500 hover:bg-rose-500 hover:text-white transition-all font-bold text-xs uppercase shadow-lg shadow-rose-500/5 border border-rose-500/20">
          Stop All
        </button>
        <button @click="startAll" class="px-6 py-2 rounded-xl bg-cyan-600 text-white hover:bg-cyan-500 transition-all font-bold text-xs uppercase shadow-xl shadow-cyan-500/20 border border-cyan-400/30">
          Run All
        </button>
      </div>
    </div>

    <div class="grid grid-cols-2 lg:grid-cols-3 gap-4 overflow-y-auto pr-2 custom-scrollbar">
      <div v-for="(s, name) in services" :key="name" 
        class="relative group p-4 rounded-2xl border transition-all duration-300 select-none cursor-pointer overflow-hidden"
        :class="s.running 
          ? 'bg-cyan-500/5 border-cyan-500/30 shadow-[inset_0_0_20px_rgba(6,182,212,0.05)]' 
          : 'bg-white/[0.02] border-white/5 hover:border-white/10'">
        
        <div class="flex justify-between items-start mb-6">
          <div class="p-2 rounded-lg bg-white/5 border border-white/5 shadow-inner">
            <component :is="getIcon(name)" class="w-5 h-5" :class="s.running ? 'text-cyan-400' : 'text-slate-500'" />
          </div>
          <div v-if="s.running" class="flex flex-col items-end">
             <span class="text-[10px] font-mono text-cyan-500/70 tracking-tighter">PID: {{ Math.floor(Math.random()*9000) }}</span>
             <span class="text-[10px] font-bold text-cyan-400 uppercase tracking-widest">Active</span>
          </div>
        </div>

        <div class="flex flex-col mb-4">
          <span class="text-sm font-black uppercase text-white group-hover:text-cyan-400 transition-colors">{{ name }}</span>
          <span class="text-[10px] text-slate-500 font-mono italic tracking-wider">Port: {{ s.port }}</span>
        </div>

        <button @click.stop="toggle(name)" 
          class="w-full py-2 rounded-lg text-[10px] font-black uppercase tracking-widest transition-all"
          :class="s.running ? 'bg-white/5 text-white/40 hover:bg-rose-500/20 hover:text-rose-500' : 'bg-white/10 text-white hover:bg-cyan-500'">
          {{ s.loading ? 'Processing...' : (s.running ? 'Terminate' : 'Start Service') }}
        </button>
      </div>
    </div>

  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { ServerIcon, GlobeAltIcon, CodeBracketIcon, CommandLineIcon, CogIcon } from '@heroicons/vue/24/solid'
import PHPIcon from '../components/icons/PHPIcon.vue'
import NginxIcon from '../components/icons/NginxIcon.vue'
import MySQLIcon from '../components/icons/MySQLIcon.vue'
import RedisIcon from '../components/icons/RedisIcon.vue'
import NodeJSIcon from '../components/icons/NodeJSIcon.vue'
import DockerIcon from '../components/icons/DockerIcon.vue'

const services = ref({
  nginx: { running: true, loading: false, port: 80 },
  php: { running: true, loading: false, port: 9000 },
  mysql: { running: false, loading: false, port: 3306 },
  redis: { running: false, loading: false, port: 6379 },
  node: { running: false, loading: false, port: 3000 },
  docker: { running: false, loading: false, port: 2375 },
})

const getIcon = (name: string) => {
  const map: any = { nginx: NginxIcon, php: PHPIcon, mysql: MySQLIcon, redis: RedisIcon, node: NodeJSIcon, docker: DockerIcon }
  return map[name] || ServerIcon
}

const toggle = (n: string) => { /* твоя логика запуска */ }
const startAll = () => { /* запуск всех */ }
const stopAll = () => { /* остановка всех */ }
</script>