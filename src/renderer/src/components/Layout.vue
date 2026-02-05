<template>
  <div class="h-screen bg-[#0d0f14] text-slate-300 flex flex-col overflow-hidden border border-white/5">
    
    <header class="h-12 flex items-center justify-between px-4 bg-white/[0.02] backdrop-blur-md select-none border-b border-white/5" style="-webkit-app-region: drag">
      
      <nav class="flex items-center space-x-1" style="-webkit-app-region: no-drag">
        <router-link to="/" class="p-2 rounded-lg hover:bg-white/5 transition-colors group" title="Dashboard">
          <Squares2X2Icon class="w-5 h-5 group-hover:text-cyan-400 transition-colors" />
        </router-link>
        <router-link to="/settings" class="p-2 rounded-lg hover:bg-white/5 transition-colors group" title="Settings">
          <AdjustmentsHorizontalIcon class="w-5 h-5 group-hover:text-cyan-400 transition-colors" />
        </router-link>
        <div class="h-4 w-px bg-white/10 mx-2"></div>
        <div class="flex items-center space-x-2 px-2 py-1 rounded-md bg-cyan-500/10 border border-cyan-500/20">
          <div class="w-1.5 h-1.5 rounded-full bg-cyan-500 animate-pulse"></div>
          <span class="text-[10px] font-bold text-cyan-500 uppercase tracking-tighter">System Ready</span>
        </div>
      </nav>

      <div class="flex items-center space-x-1" style="-webkit-app-region: no-drag">
        <button @click="control('minimize')" class="w-8 h-8 flex items-center justify-center rounded-md hover:bg-white/5 transition-colors group">
          <MinusIcon class="w-3.5 h-3.5 text-slate-500 group-hover:text-white" />
        </button>
        <button @click="control('maximize')" class="w-8 h-8 flex items-center justify-center rounded-md hover:bg-white/5 transition-colors group">
          <ArrowsPointingOutIcon class="w-3 h-3 text-slate-500 group-hover:text-white" />
        </button>
        <button @click="control('close')" class="w-8 h-8 flex items-center justify-center rounded-md hover:bg-rose-500/20 group transition-colors">
          <XMarkIcon class="w-3.5 h-3.5 text-slate-500 group-hover:text-rose-500" />
        </button>
      </div>
    </header>

    <main class="flex-1 overflow-hidden relative">
      <router-view v-slot="{ Component }">
        <transition name="fade" mode="out-in">
          <component :is="Component" />
        </transition>
      </router-view>
    </main>

    <footer class="h-8 bg-black/40 border-t border-white/5 px-4 flex items-center justify-between text-[10px] font-medium tracking-wider uppercase opacity-60">
      <div class="flex items-center space-x-4 italic">
        <span>MEM: 1.2GB</span>
        <span>CPU: 4%</span>
      </div>
      <div class="flex items-center space-x-2">
        <span>Sokhumi, GEO</span>
        <div class="w-1 h-1 rounded-full bg-slate-500"></div>
        <span>2026</span>
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { 
  Squares2X2Icon, AdjustmentsHorizontalIcon, 
  MinusIcon, ArrowsPointingOutIcon, XMarkIcon 
} from '@heroicons/vue/24/outline'

const control = (action: string) => window.electron?.send('window-control', action)
</script>