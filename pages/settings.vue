<template>
  <div class="min-h-screen p-4">
    <div class="max-w-md mx-auto">
      <!-- Header -->
      <div class="mb-6">
        <h1 class="text-2xl font-bold text-foreground mb-2">Pengaturan</h1>
        <p class="text-muted-foreground">Sesuaikan aplikasi sesuai preferensi Anda</p>
      </div>

      <!-- Settings Sections -->
      <div class="space-y-6">
        
        <!-- Account Section -->
        <div class="bg-card border border-border rounded-lg p-4">
          <h3 class="font-semibold mb-3 flex items-center gap-2">
            <UserIcon class="h-4 w-4 text-primary" />
            Akun & Profil
          </h3>
          <div class="space-y-3">
            <div class="flex items-center justify-between hover:bg-accent/50 p-2 rounded-lg transition-colors cursor-pointer">
              <div>
                <div class="text-sm font-medium">John Doe</div>
                <div class="text-xs text-muted-foreground">john.doe@example.com</div>
              </div>
              <ChevronRight class="h-4 w-4 text-muted-foreground" />
            </div>
          </div>
        </div>

        <!-- Appearance & Themes Section -->
        <div class="bg-card border border-border rounded-lg p-4">
          <h3 class="font-semibold mb-4 flex items-center gap-2">
            <Palette class="h-4 w-4 text-primary" />
            Tampilan & Tema
          </h3>
          
          <!-- Dark Mode Toggle -->
          <div class="mb-4 p-3 border border-border rounded-lg">
            <div class="flex items-center gap-3 mb-3">
              <div class="w-8 h-8 bg-gray-100 dark:bg-gray-800 rounded-lg flex items-center justify-center">
                <Moon class="h-4 w-4 text-gray-600 dark:text-gray-400" />
              </div>
              <span class="text-sm font-medium">Mode Tema</span>
            </div>
            
            <!-- Theme Mode Options -->
            <div class="space-y-2">
              <div 
                @click="setColorMode('light')"
                class="flex items-center justify-between p-2 rounded-lg cursor-pointer transition-colors"
                :class="colorMode.value === 'light' ? 'bg-primary/10 border border-primary/20' : 'hover:bg-accent/50'"
              >
                <div class="flex items-center gap-3">
                  <Sun class="h-4 w-4 text-yellow-500" />
                  <span class="text-sm">Mode Terang</span>
                </div>
                <div v-if="colorMode.value === 'light'" class="w-4 h-4 bg-primary rounded-full flex items-center justify-center">
                  <Check class="h-2.5 w-2.5 text-primary-foreground" />
                </div>
              </div>
              
              <div 
                @click="setColorMode('dark')"
                class="flex items-center justify-between p-2 rounded-lg cursor-pointer transition-colors"
                :class="colorMode.value === 'dark' ? 'bg-primary/10 border border-primary/20' : 'hover:bg-accent/50'"
              >
                <div class="flex items-center gap-3">
                  <Moon class="h-4 w-4 text-blue-500" />
                  <span class="text-sm">Mode Gelap</span>
                </div>
                <div v-if="colorMode.value === 'dark'" class="w-4 h-4 bg-primary rounded-full flex items-center justify-center">
                  <Check class="h-2.5 w-2.5 text-primary-foreground" />
                </div>
              </div>
              
              <div 
                @click="setColorMode('system')"
                class="flex items-center justify-between p-2 rounded-lg cursor-pointer transition-colors"
                :class="colorMode.value === 'system' ? 'bg-primary/10 border border-primary/20' : 'hover:bg-accent/50'"
              >
                <div class="flex items-center gap-3">
                  <Monitor class="h-4 w-4 text-purple-500" />
                  <div>
                    <div class="text-sm">Ikuti Sistem</div>
                    <div class="text-xs text-muted-foreground">{{ systemThemeText }}</div>
                  </div>
                </div>
                <div v-if="colorMode.value === 'system'" class="w-4 h-4 bg-primary rounded-full flex items-center justify-center">
                  <Check class="h-2.5 w-2.5 text-primary-foreground" />
                </div>
              </div>
            </div>
          </div>

          <!-- Theme Switcher -->
          <div class="border-t pt-4">
            <div class="flex items-center gap-2 mb-4">
              <Paintbrush class="h-4 w-4 text-primary" />
              <span class="text-sm font-medium">Pilih Tema Warna</span>
            </div>
            
            <!-- Theme Grid -->
            <div class="grid grid-cols-2 gap-3 mb-4">
              <div 
                v-for="theme in themes" 
                :key="theme.id"
                @click="setTheme(theme.id)"
                class="relative p-3 border-2 rounded-lg cursor-pointer transition-all duration-200 hover:scale-105"
                :class="{
                  'border-primary bg-primary/5': currentTheme === theme.id,
                  'border-border hover:border-primary/50': currentTheme !== theme.id
                }"
              >
                <!-- Theme Preview Circles -->
                <div class="flex items-center gap-1.5 mb-2">
                  <div 
                    class="w-3 h-3 rounded-full border border-white/20 shadow-sm"
                    :style="{ backgroundColor: theme.primary }"
                  ></div>
                  <div 
                    class="w-2.5 h-2.5 rounded-full border border-white/20 shadow-sm"
                    :style="{ backgroundColor: theme.secondary }"
                  ></div>
                  <div 
                    class="w-2 h-2 rounded-full border border-white/20 shadow-sm"
                    :style="{ backgroundColor: theme.accent }"
                  ></div>
                </div>
                
                <!-- Theme Name -->
                <div class="text-xs font-medium text-foreground">{{ theme.name }}</div>
                <div class="text-xs text-muted-foreground truncate">{{ theme.description }}</div>
                
                <!-- Active Indicator -->
                <div 
                  v-if="currentTheme === theme.id"
                  class="absolute top-2 right-2 w-4 h-4 bg-primary rounded-full flex items-center justify-center"
                >
                  <Check class="h-2.5 w-2.5 text-primary-foreground" />
                </div>
              </div>
            </div>
            
            <!-- Current Theme Preview -->
            <div class="bg-accent/50 rounded-lg p-3">
              <div class="text-xs font-medium text-muted-foreground mb-2">Preview Tema Aktif</div>
              <div class="flex items-center gap-2">
                <div class="w-6 h-6 bg-primary rounded-md flex items-center justify-center">
                  <Star class="h-3 w-3 text-primary-foreground" />
                </div>
                <div class="text-sm">{{ currentThemeData?.name || 'Ocean Blue' }}</div>
              </div>
            </div>
          </div>
        </div>

        <!-- Notifications Section -->
        <div class="bg-card border border-border rounded-lg p-4">
          <h3 class="font-semibold mb-3 flex items-center gap-2">
            <Bell class="h-4 w-4 text-primary" />
            Notifikasi
          </h3>
          <div class="space-y-3">
            <div class="flex items-center justify-between">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-blue-100 dark:bg-blue-900/30 rounded-lg flex items-center justify-center">
                  <Smartphone class="h-4 w-4 text-blue-600 dark:text-blue-400" />
                </div>
                <div>
                  <div class="text-sm font-medium">Push Notifications</div>
                  <div class="text-xs text-muted-foreground">Notifikasi langsung</div>
                </div>
              </div>
              <button class="relative inline-flex h-6 w-11 items-center rounded-full bg-primary transition-colors focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2">
                <span class="inline-block h-4 w-4 transform rounded-full bg-white transition-transform translate-x-6" />
              </button>
            </div>
            
            <div class="flex items-center justify-between">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-green-100 dark:bg-green-900/30 rounded-lg flex items-center justify-center">
                  <Mail class="h-4 w-4 text-green-600 dark:text-green-400" />
                </div>
                <div>
                  <div class="text-sm font-medium">Email Notifications</div>
                  <div class="text-xs text-muted-foreground">Notifikasi via email</div>
                </div>
              </div>
              <button class="relative inline-flex h-6 w-11 items-center rounded-full bg-gray-200 transition-colors focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2">
                <span class="inline-block h-4 w-4 transform rounded-full bg-white transition-transform translate-x-1" />
              </button>
            </div>

            <div class="flex items-center justify-between">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-purple-100 dark:bg-purple-900/30 rounded-lg flex items-center justify-center">
                  <Volume2 class="h-4 w-4 text-purple-600 dark:text-purple-400" />
                </div>
                <div>
                  <div class="text-sm font-medium">Suara & Getaran</div>
                  <div class="text-xs text-muted-foreground">Feedback haptic</div>
                </div>
              </div>
              <button class="relative inline-flex h-6 w-11 items-center rounded-full bg-primary transition-colors focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2">
                <span class="inline-block h-4 w-4 transform rounded-full bg-white transition-transform translate-x-6" />
              </button>
            </div>
          </div>
        </div>

        <!-- Privacy & Security Section -->
        <div class="bg-card border border-border rounded-lg p-4">
          <h3 class="font-semibold mb-3 flex items-center gap-2">
            <Shield class="h-4 w-4 text-primary" />
            Privasi & Keamanan
          </h3>
          <div class="space-y-3">
            <div class="flex items-center justify-between hover:bg-accent/50 p-2 rounded-lg transition-colors cursor-pointer">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-red-100 dark:bg-red-900/30 rounded-lg flex items-center justify-center">
                  <Key class="h-4 w-4 text-red-600 dark:text-red-400" />
                </div>
                <div>
                  <div class="text-sm font-medium">Ubah Password</div>
                  <div class="text-xs text-muted-foreground">Terakhir diubah 3 bulan lalu</div>
                </div>
              </div>
              <ChevronRight class="h-4 w-4 text-muted-foreground" />
            </div>
            
            <div class="flex items-center justify-between hover:bg-accent/50 p-2 rounded-lg transition-colors cursor-pointer">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-orange-100 dark:bg-orange-900/30 rounded-lg flex items-center justify-center">
                  <Fingerprint class="h-4 w-4 text-orange-600 dark:text-orange-400" />
                </div>
                <div>
                  <div class="text-sm font-medium">Autentikasi Biometrik</div>
                  <div class="text-xs text-muted-foreground">Fingerprint & Face ID</div>
                </div>
              </div>
              <div class="flex items-center gap-2">
                <div class="text-xs bg-green-100 dark:bg-green-900/30 text-green-700 dark:text-green-400 px-2 py-1 rounded-full">Aktif</div>
                <ChevronRight class="h-4 w-4 text-muted-foreground" />
              </div>
            </div>

            <div class="flex items-center justify-between hover:bg-accent/50 p-2 rounded-lg transition-colors cursor-pointer">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-blue-100 dark:bg-blue-900/30 rounded-lg flex items-center justify-center">
                  <Database class="h-4 w-4 text-blue-600 dark:text-blue-400" />
                </div>
                <div>
                  <div class="text-sm font-medium">Data & Privasi</div>
                  <div class="text-xs text-muted-foreground">Kelola data pribadi</div>
                </div>
              </div>
              <ChevronRight class="h-4 w-4 text-muted-foreground" />
            </div>
          </div>
        </div>

        <!-- App Preferences Section -->
        <div class="bg-card border border-border rounded-lg p-4">
          <h3 class="font-semibold mb-3 flex items-center gap-2">
            <Settings class="h-4 w-4 text-primary" />
            Preferensi Aplikasi
          </h3>
          <div class="space-y-3">
            <div class="flex items-center justify-between">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-green-100 dark:bg-green-900/30 rounded-lg flex items-center justify-center">
                  <Download class="h-4 w-4 text-green-600 dark:text-green-400" />
                </div>
                <div>
                  <div class="text-sm font-medium">Auto-Update</div>
                  <div class="text-xs text-muted-foreground">Update otomatis</div>
                </div>
              </div>
              <button class="relative inline-flex h-6 w-11 items-center rounded-full bg-primary transition-colors focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2">
                <span class="inline-block h-4 w-4 transform rounded-full bg-white transition-transform translate-x-6" />
              </button>
            </div>

            <div class="flex items-center justify-between hover:bg-accent/50 p-2 rounded-lg transition-colors cursor-pointer">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-purple-100 dark:bg-purple-900/30 rounded-lg flex items-center justify-center">
                  <HardDrive class="h-4 w-4 text-purple-600 dark:text-purple-400" />
                </div>
                <div>
                  <div class="text-sm font-medium">Penyimpanan</div>
                  <div class="text-xs text-muted-foreground">142 MB digunakan</div>
                </div>
              </div>
              <button class="text-sm text-primary font-medium hover:text-primary/80 transition-colors">
                Bersihkan
              </button>
            </div>

            <div class="flex items-center justify-between hover:bg-accent/50 p-2 rounded-lg transition-colors cursor-pointer">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-blue-100 dark:bg-blue-900/30 rounded-lg flex items-center justify-center">
                  <Globe class="h-4 w-4 text-blue-600 dark:text-blue-400" />
                </div>
                <div>
                  <div class="text-sm font-medium">Bahasa</div>
                  <div class="text-xs text-muted-foreground">Bahasa Indonesia</div>
                </div>
              </div>
              <ChevronRight class="h-4 w-4 text-muted-foreground" />
            </div>
          </div>
        </div>

        <!-- Support & About Section -->
        <div class="bg-card border border-border rounded-lg p-4">
          <h3 class="font-semibold mb-3 flex items-center gap-2">
            <HelpCircle class="h-4 w-4 text-primary" />
            Bantuan & Informasi
          </h3>
          <div class="space-y-3">
            <div class="flex items-center justify-between hover:bg-accent/50 p-2 rounded-lg transition-colors cursor-pointer">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-yellow-100 dark:bg-yellow-900/30 rounded-lg flex items-center justify-center">
                  <BookOpen class="h-4 w-4 text-yellow-600 dark:text-yellow-400" />
                </div>
                <span class="text-sm">Pusat Bantuan</span>
              </div>
              <ChevronRight class="h-4 w-4 text-muted-foreground" />
            </div>
            
            <div class="flex items-center justify-between hover:bg-accent/50 p-2 rounded-lg transition-colors cursor-pointer">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-green-100 dark:bg-green-900/30 rounded-lg flex items-center justify-center">
                  <MessageCircle class="h-4 w-4 text-green-600 dark:text-green-400" />
                </div>
                <span class="text-sm">Hubungi Support</span>
              </div>
              <ChevronRight class="h-4 w-4 text-muted-foreground" />
            </div>

            <div class="flex items-center justify-between hover:bg-accent/50 p-2 rounded-lg transition-colors cursor-pointer">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-red-100 dark:bg-red-900/30 rounded-lg flex items-center justify-center">
                  <Bug class="h-4 w-4 text-red-600 dark:text-red-400" />
                </div>
                <span class="text-sm">Laporkan Bug</span>
              </div>
              <ChevronRight class="h-4 w-4 text-muted-foreground" />
            </div>

            <div class="flex items-center justify-between hover:bg-accent/50 p-2 rounded-lg transition-colors cursor-pointer">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-gray-100 dark:bg-gray-800 rounded-lg flex items-center justify-center">
                  <Info class="h-4 w-4 text-gray-600 dark:text-gray-400" />
                </div>
                <div>
                  <div class="text-sm font-medium">Versi Aplikasi</div>
                  <div class="text-xs text-muted-foreground">v1.2.3 (Build 456)</div>
                </div>
              </div>
              <ExternalLink class="h-4 w-4 text-muted-foreground" />
            </div>
          </div>
        </div>

        <!-- Legal Section -->
        <div class="bg-card border border-border rounded-lg p-4">
          <h3 class="font-semibold mb-3 flex items-center gap-2">
            <FileText class="h-4 w-4 text-primary" />
            Legal & Kebijakan
          </h3>
          <div class="space-y-3">
            <div class="flex items-center justify-between hover:bg-accent/50 p-2 rounded-lg transition-colors cursor-pointer">
              <span class="text-sm">Syarat & Ketentuan</span>
              <ChevronRight class="h-4 w-4 text-muted-foreground" />
            </div>
            <div class="flex items-center justify-between hover:bg-accent/50 p-2 rounded-lg transition-colors cursor-pointer">
              <span class="text-sm">Kebijakan Privasi</span>
              <ChevronRight class="h-4 w-4 text-muted-foreground" />
            </div>
            <div class="flex items-center justify-between hover:bg-accent/50 p-2 rounded-lg transition-colors cursor-pointer">
              <span class="text-sm">Lisensi Open Source</span>
              <ChevronRight class="h-4 w-4 text-muted-foreground" />
            </div>
          </div>
        </div>

        <!-- Danger Zone -->
        <div class="bg-destructive/5 border border-destructive/20 rounded-lg p-4">
          <h3 class="font-semibold mb-4 flex items-center gap-2 text-destructive">
            <AlertTriangle class="h-4 w-4" />
            Zona Berbahaya
          </h3>
          <div class="space-y-3">
            <button class="w-full py-3 bg-destructive text-destructive-foreground rounded-lg font-medium hover:bg-destructive/90 transition-colors flex items-center justify-center gap-2">
              <LogOut class="h-4 w-4" />
              Keluar dari Akun
            </button>
            <button class="w-full py-3 border border-destructive text-destructive rounded-lg font-medium hover:bg-destructive/10 transition-colors flex items-center justify-center gap-2">
              <Trash2 class="h-4 w-4" />
              Hapus Akun Permanen
            </button>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>
import { 
  Settings, 
  Bell, 
  Shield, 
  Palette,
  Paintbrush,
  ChevronRight, 
  Info, 
  User as UserIcon, 
  HelpCircle,
  AlertTriangle,
  ExternalLink,
  Moon,
  Sun,
  Monitor,
  Star,
  Check,
  Smartphone,
  Mail,
  Volume2,
  Key,
  Fingerprint,
  Database,
  Download,
  HardDrive,
  Globe,
  BookOpen,
  MessageCircle,
  Bug,
  FileText,
  LogOut,
  Trash2
} from 'lucide-vue-next'

// Color mode for dark/light toggle
const colorMode = useColorMode()

// System theme detection
const systemTheme = ref('light')
const systemThemeText = computed(() => {
  return `Saat ini: ${systemTheme.value === 'dark' ? 'gelap' : 'terang'}`
})

// Detect system theme preference
const detectSystemTheme = () => {
  if (process.client) {
    const mediaQuery = window.matchMedia('(prefers-color-scheme: dark)')
    systemTheme.value = mediaQuery.matches ? 'dark' : 'light'
    
    // Listen for system theme changes
    mediaQuery.addEventListener('change', (e) => {
      systemTheme.value = e.matches ? 'dark' : 'light'
    })
  }
}

// Set color mode function
const setColorMode = (mode) => {
  colorMode.preference = mode
  
  // Apply theme changes immediately if needed
  if (mode === 'system') {
    detectSystemTheme()
  }
}

// Legacy toggle function for backward compatibility
const toggleDarkMode = () => {
  if (colorMode.value === 'dark') {
    setColorMode('light')
  } else {
    setColorMode('dark')
  }
}

// Theme definitions
const themes = [
  {
    id: 'ocean',
    name: 'Ocean Blue',
    description: 'Biru laut tenang',
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
    description: 'Orange matahari',
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
    description: 'Biru midnight',
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
  applyTheme(themeId)
  
  // Save to localStorage
  if (process.client) {
    localStorage.setItem('selected-theme', themeId)
  }
}

// Apply theme function with system theme support
const applyTheme = (themeId) => {
  if (process.client) {
    const root = document.documentElement
    
    // Remove existing theme classes
    themes.forEach(theme => {
      root.classList.remove(`theme-${theme.id}`)
    })
    
    // Add new theme class
    root.classList.add(`theme-${themeId}`)
    
    // Handle system theme if color mode is system
    if (colorMode.value === 'system') {
      detectSystemTheme()
    }
    
    // Update mobile container styles with a slight delay to ensure CSS variables are updated
    setTimeout(() => {
      const container = document.querySelector('.mobile-container')
      if (container) {
        container.style.background = 'hsl(var(--background))'
        container.style.boxShadow = '0 0 0 1px hsl(var(--border))'
      }
    }, 100)
  }
}

// Initialize theme and system detection on mount
onMounted(() => {
  if (process.client) {
    // Detect system theme preference
    detectSystemTheme()
    
    // Load saved theme
    const savedTheme = localStorage.getItem('selected-theme') || 'ocean'
    currentTheme.value = savedTheme
    applyTheme(savedTheme)
    
    // Watch for color mode changes to re-apply theme
    watch(() => colorMode.value, () => {
      applyTheme(currentTheme.value)
    })
  }
})

useHead({
  title: 'Pengaturan - Mobile App'
})
</script>