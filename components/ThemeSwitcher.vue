<template>
    <div class="space-y-4">
      <!-- Theme Selector Header -->
      <div class="flex items-center gap-2 mb-4">
        <Palette class="h-5 w-5 text-primary" />
        <h3 class="font-semibold text-foreground">Pilih Tema Warna</h3>
      </div>
      
      <!-- Theme Grid -->
      <div class="grid grid-cols-2 gap-3">
        <div 
          v-for="theme in themes" 
          :key="theme.id"
          @click="setTheme(theme.id)"
          class="relative p-4 border-2 rounded-lg cursor-pointer transition-all duration-200 hover:scale-105"
          :class="{
            'border-primary bg-primary/5': currentTheme === theme.id,
            'border-border hover:border-primary/50': currentTheme !== theme.id
          }"
        >
          <!-- Theme Preview Circles -->
          <div class="flex items-center gap-2 mb-3">
            <div 
              class="w-4 h-4 rounded-full border border-white/20"
              :style="{ backgroundColor: theme.primary }"
            ></div>
            <div 
              class="w-3 h-3 rounded-full border border-white/20"
              :style="{ backgroundColor: theme.secondary }"
            ></div>
            <div 
              class="w-2 h-2 rounded-full border border-white/20"
              :style="{ backgroundColor: theme.accent }"
            ></div>
          </div>
          
          <!-- Theme Name -->
          <div class="text-sm font-medium text-foreground">{{ theme.name }}</div>
          <div class="text-xs text-muted-foreground">{{ theme.description }}</div>
          
          <!-- Active Indicator -->
          <div 
            v-if="currentTheme === theme.id"
            class="absolute top-2 right-2 w-5 h-5 bg-primary rounded-full flex items-center justify-center"
          >
            <Check class="h-3 w-3 text-primary-foreground" />
          </div>
        </div>
      </div>
      
      <!-- Preview Card -->
      <div class="mt-6 p-4 bg-card border border-border rounded-lg">
        <h4 class="font-medium mb-2">Preview</h4>
        <div class="space-y-2">
          <div class="flex items-center gap-2">
            <div class="w-8 h-8 bg-primary rounded-lg flex items-center justify-center">
              <Star class="h-4 w-4 text-primary-foreground" />
            </div>
            <div>
              <div class="text-sm font-medium">{{ currentThemeData?.name }}</div>
              <div class="text-xs text-muted-foreground">Primary color preview</div>
            </div>
          </div>
          <button class="w-full py-2 bg-primary text-primary-foreground rounded-md text-sm font-medium">
            Button Example
          </button>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { Palette, Check, Star } from 'lucide-vue-next'
  
  // Theme definitions
  const themes = [
    {
      id: 'ocean',
      name: 'Ocean Blue',
      description: 'Biru laut yang tenang',
      primary: '#3b82f6',
      secondary: '#f1f5f9',
      accent: '#e2e8f0'
    },
    {
      id: 'emerald',
      name: 'Emerald Green',
      description: 'Hijau emerald segar',
      primary: '#059669',
      secondary: '#f0fdf4',
      accent: '#dcfce7'
    },
    {
      id: 'sunset',
      name: 'Sunset Orange',
      description: 'Orange hangat matahari',
      primary: '#ea580c',
      secondary: '#fefce8',
      accent: '#fed7aa'
    },
    {
      id: 'royal',
      name: 'Royal Purple',
      description: 'Ungu royal mewah',
      primary: '#7c3aed',
      secondary: '#faf5ff',
      accent: '#e9d5ff'
    },
    {
      id: 'crimson',
      name: 'Crimson Red',
      description: 'Merah crimson bold',
      primary: '#dc2626',
      secondary: '#fef2f2',
      accent: '#fecaca'
    },
    {
      id: 'mint',
      name: 'Teal Mint',
      description: 'Teal mint modern',
      primary: '#0d9488',
      secondary: '#f0fdfa',
      accent: '#ccfbf1'
    },
    {
      id: 'rose',
      name: 'Rose Gold',
      description: 'Rose gold feminine',
      primary: '#e11d48',
      secondary: '#fff1f2',
      accent: '#fecdd3'
    },
    {
      id: 'midnight',
      name: 'Midnight Blue',
      description: 'Biru midnight elegan',
      primary: '#1e293b',
      secondary: '#f8fafc',
      accent: '#e2e8f0'
    }
  ]
  
  // Current theme state
  const currentTheme = ref('ocean')
  
  // Get current theme data
  const currentThemeData = computed(() => {
    return themes.find(theme => theme.id === currentTheme.value)
  })
  
  // Set theme function
  const setTheme = (themeId) => {
    currentTheme.value = themeId
    
    // Apply theme to document
    applyTheme(themeId)
    
    // Save to localStorage
    if (process.client) {
      localStorage.setItem('selected-theme', themeId)
    }
  }
  
  // Apply theme function
  const applyTheme = (themeId) => {
    if (process.client) {
      const root = document.documentElement
      
      // Remove existing theme classes
      themes.forEach(theme => {
        root.classList.remove(`theme-${theme.id}`)
      })
      
      // Add new theme class
      root.classList.add(`theme-${themeId}`)
      
      // Update mobile container background
      const container = document.querySelector('.mobile-container')
      if (container) {
        container.style.background = 'hsl(var(--background))'
        container.style.boxShadow = '0 0 0 1px hsl(var(--border))'
      }
    }
  }
  
  // Initialize theme on mount
  onMounted(() => {
    if (process.client) {
      const savedTheme = localStorage.getItem('selected-theme') || 'ocean'
      currentTheme.value = savedTheme
      applyTheme(savedTheme)
    }
  })
  </script>