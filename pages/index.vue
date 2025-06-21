<template>
  <div class="min-h-screen p-4">
    <div class="max-w-md mx-auto">
      <!-- Header -->
      <div class="mb-6">
        <h1 class="text-2xl font-bold text-foreground mb-2">Selamat Datang</h1>
        <p class="text-muted-foreground">Ini adalah halaman beranda aplikasi Anda</p>
      </div>

      <!-- Welcome Card -->
      <div class="bg-card border border-border rounded-lg p-6 mb-4">
        <div class="flex items-center gap-3 mb-4">
          <div class="w-12 h-12 bg-primary/10 rounded-full flex items-center justify-center">
            <Home class="h-6 w-6 text-primary" />
          </div>
          <div>
            <h2 class="text-lg font-semibold">Halaman Beranda</h2>
            <p class="text-sm text-muted-foreground">Template UI Mobile</p>
          </div>
        </div>
        <p class="text-muted-foreground mb-4">
          Template ini menggunakan Nuxt 3 dengan Shadcn UI. Layout dirancang khusus untuk tampilan mobile-first 
          dengan lebar tetap bahkan di desktop.
        </p>
        <div class="flex items-center gap-2 text-sm text-muted-foreground">
          <div class="w-2 h-2 bg-green-500 rounded-full"></div>
          <span>Status: Siap Digunakan</span>
        </div>
      </div>

      <!-- Quick Actions -->
      <div class="grid grid-cols-2 gap-3 mb-6">
        <div class="bg-primary/10 border border-primary/20 rounded-lg p-4 text-center hover:bg-primary/20 transition-colors cursor-pointer">
          <Star class="h-6 w-6 text-primary mx-auto mb-2" />
          <div class="text-primary font-semibold text-sm">Fitur 1</div>
          <div class="text-xs text-muted-foreground mt-1">Aksi cepat</div>
        </div>
        <div class="bg-secondary border border-border rounded-lg p-4 text-center hover:bg-accent transition-colors cursor-pointer">
          <Zap class="h-6 w-6 text-secondary-foreground mx-auto mb-2" />
          <div class="font-semibold text-sm">Fitur 2</div>
          <div class="text-xs text-muted-foreground mt-1">Aksi cepat</div>
        </div>
      </div>

      <!-- Stats Cards -->
      <div class="space-y-3">
        <div class="bg-card border border-border rounded-lg p-4">
          <div class="flex items-center justify-between">
            <div>
              <div class="text-2xl font-bold text-foreground">42</div>
              <div class="text-sm text-muted-foreground">Total Items</div>
            </div>
            <div class="w-10 h-10 bg-blue-100 rounded-lg flex items-center justify-center">
              <BarChart3 class="h-5 w-5 text-blue-600" />
            </div>
          </div>
        </div>
        
        <div class="bg-card border border-border rounded-lg p-4">
          <div class="flex items-center justify-between">
            <div>
              <div class="text-2xl font-bold text-foreground">12</div>
              <div class="text-sm text-muted-foreground">Favorit</div>
            </div>
            <div class="w-10 h-10 bg-red-100 rounded-lg flex items-center justify-center">
              <Heart class="h-5 w-5 text-red-600" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { Home, Star, Zap, BarChart3, Heart } from 'lucide-vue-next'

useHead({
  title: 'Beranda - Mobile App'
})
</script>