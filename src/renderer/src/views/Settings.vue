<template>
  <div class="h-full flex flex-col bg-[#0d0f14]">
    
    <div class="px-6 py-4 border-b border-white/5 flex items-center justify-between shrink-0">
      <div class="flex items-center space-x-3">
        <CogIcon class="w-5 h-5 text-cyan-500" />
        <h1 class="text-sm font-black uppercase tracking-widest text-white">Settings</h1>
      </div>
      <button class="px-4 py-1.5 bg-cyan-600 hover:bg-cyan-500 text-white text-[10px] font-bold uppercase rounded-md transition-all shadow-lg shadow-cyan-900/20">
        Save
      </button>
    </div>

    <div class="flex-1 overflow-y-auto custom-scrollbar p-6">
      <div class="grid grid-cols-2 gap-4">
        
        <div class="bg-white/[0.02] border border-white/5 rounded-lg p-4 space-y-4">
          <h2 class="text-[10px] font-bold text-slate-500 uppercase tracking-widest border-b border-white/5 pb-2">General</h2>
          
          <div class="space-y-3">
            <div class="flex items-center justify-between">
              <span class="text-xs text-slate-300">Port Range</span>
              <div class="flex items-center space-x-2 w-32">
                <input type="number" value="80" class="w-full bg-black/40 border border-white/10 rounded px-2 py-1 text-xs text-cyan-400 outline-none" />
                <input type="number" value="443" class="w-full bg-black/40 border border-white/10 rounded px-2 py-1 text-xs text-cyan-400 outline-none" />
              </div>
            </div>

            <label class="flex items-center justify-between cursor-pointer group">
              <span class="text-xs text-slate-300 group-hover:text-white transition-colors">Autostart services</span>
              <input type="checkbox" checked class="w-3 h-3 accent-cyan-500" />
            </label>
            
            <div class="flex items-center justify-between">
              <span class="text-xs text-slate-300">UI Theme</span>
              <select class="bg-black/40 border border-white/10 rounded px-2 py-1 text-xs text-slate-300 outline-none">
                <option>Dark</option>
                <option>Light</option>
              </select>
            </div>
          </div>
        </div>

        <div class="bg-white/[0.02] border border-white/5 rounded-lg p-4 space-y-4">
          <h2 class="text-[10px] font-bold text-slate-500 uppercase tracking-widest border-b border-white/5 pb-2">Environment</h2>
          <div class="space-y-3">
            <div class="flex items-center justify-between">
              <span class="text-xs text-slate-300">PHP</span>
              <select class="w-24 bg-black/40 border border-white/10 rounded px-2 py-1 text-xs text-slate-300 outline-none font-mono">
                <option>8.2.0</option>
                <option>8.1.0</option>
              </select>
            </div>
            <div class="flex items-center justify-between">
              <span class="text-xs text-slate-300">Node.js</span>
              <select class="w-24 bg-black/40 border border-white/10 rounded px-2 py-1 text-xs text-slate-300 outline-none font-mono">
                <option>20.x</option>
                <option>18.x</option>
              </select>
            </div>
            <div class="flex items-center justify-between">
              <span class="text-xs text-slate-300">Server</span>
              <div class="flex bg-black/40 p-0.5 rounded border border-white/5">
                <button class="px-2 py-1 text-[9px] font-bold uppercase bg-cyan-600 text-white rounded-[3px]">Nginx</button>
                <button class="px-2 py-1 text-[9px] font-bold uppercase text-slate-500">Apache</button>
              </div>
            </div>
          </div>
        </div>

        <div class="col-span-2 bg-white/[0.02] border border-white/5 rounded-lg p-4 flex items-center justify-between">
          <div class="flex items-center space-x-4">
            <ShieldCheckIcon class="w-5 h-5 text-emerald-500" />
            <div>
              <p class="text-[10px] font-bold text-slate-500 uppercase">Domain & SSL</p>
              <p class="text-xs text-slate-200 font-mono">Local dev: <span class="text-cyan-400">*.test</span></p>
            </div>
          </div>
          <button class="px-3 py-1 border border-white/10 hover:bg-white/5 rounded text-[10px] font-bold text-slate-400 uppercase transition-all">
            Update Cert
          </button>
        </div>

        <div class="col-span-2 bg-white/[0.02] border border-white/5 rounded-lg p-4 space-y-4">
          <h2 class="text-[10px] font-bold text-slate-500 uppercase tracking-widest border-b border-white/5 pb-2">Database Ports</h2>
          <div class="grid grid-cols-3 gap-4">
            <div class="space-y-1">
              <span class="text-[9px] text-slate-500 uppercase block">MySQL</span>
              <input type="number" value="3306" class="w-full bg-black/40 border border-white/10 rounded px-2 py-1 text-xs text-slate-300 outline-none focus:border-cyan-500/50" />
            </div>
            <div class="space-y-1">
              <span class="text-[9px] text-slate-500 uppercase block">PostgreSQL</span>
              <input type="number" value="5432" class="w-full bg-black/40 border border-white/10 rounded px-2 py-1 text-xs text-slate-300 outline-none focus:border-cyan-500/50" />
            </div>
            <div class="space-y-1">
              <span class="text-[9px] text-slate-500 uppercase block">Redis</span>
              <input type="number" value="6379" class="w-full bg-black/40 border border-white/10 rounded px-2 py-1 text-xs text-slate-300 outline-none focus:border-cyan-500/50" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { CogIcon, ShieldCheckIcon } from '@heroicons/vue/24/outline'
</script>

<style scoped>
/* Тонкий современный скроллбар */
.custom-scrollbar::-webkit-scrollbar {
  width: 4px;
}
.custom-scrollbar::-webkit-scrollbar-track {
  background: transparent;
}
.custom-scrollbar::-webkit-scrollbar-thumb {
  background: rgba(255, 255, 255, 0.05);
  border-radius: 10px;
}
.custom-scrollbar::-webkit-scrollbar-thumb:hover {
  background: rgba(6, 182, 212, 0.3);
}
</style>