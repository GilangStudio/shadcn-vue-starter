<template>
  <div class="min-h-screen p-4">
    <div class="max-w-md mx-auto">
      <!-- Header -->
      <div class="mb-6">
        <h1 class="text-2xl font-bold text-foreground mb-2">Pencarian</h1>
        <p class="text-muted-foreground">Cari apa yang Anda butuhkan</p>
      </div>

      <!-- Search Input -->
      <div class="mb-6">
        <div class="relative">
          <Search class="absolute left-3 top-1/2 transform -translate-y-1/2 h-4 w-4 text-muted-foreground" />
          <input 
            type="text" 
            placeholder="Ketik untuk mencari..."
            class="w-full pl-10 pr-4 py-3 bg-background border border-border rounded-lg focus:outline-none focus:ring-2 focus:ring-primary focus:border-transparent transition-all"
          />
        </div>
      </div>

      <!-- Filter Chips -->
      <div class="flex gap-2 mb-6 overflow-x-auto pb-2">
        <div class="flex-shrink-0 px-3 py-1 bg-primary text-primary-foreground rounded-full text-sm font-medium">
          Semua
        </div>
        <div class="flex-shrink-0 px-3 py-1 bg-secondary text-secondary-foreground rounded-full text-sm hover:bg-accent transition-colors cursor-pointer">
          Kategori 1
        </div>
        <div class="flex-shrink-0 px-3 py-1 bg-secondary text-secondary-foreground rounded-full text-sm hover:bg-accent transition-colors cursor-pointer">
          Kategori 2
        </div>
        <div class="flex-shrink-0 px-3 py-1 bg-secondary text-secondary-foreground rounded-full text-sm hover:bg-accent transition-colors cursor-pointer">
          Kategori 3
        </div>
      </div>

      <!-- Recent Searches -->
      <div class="mb-6">
        <h3 class="text-sm font-semibold text-foreground mb-3">Pencarian Terkini</h3>
        <div class="space-y-2">
          <div class="flex items-center gap-3 p-3 rounded-lg hover:bg-accent transition-colors cursor-pointer">
            <Clock class="h-4 w-4 text-muted-foreground" />
            <span class="text-sm">Pencarian sebelumnya 1</span>
            <X class="h-4 w-4 text-muted-foreground ml-auto" />
          </div>
          <div class="flex items-center gap-3 p-3 rounded-lg hover:bg-accent transition-colors cursor-pointer">
            <Clock class="h-4 w-4 text-muted-foreground" />
            <span class="text-sm">Pencarian sebelumnya 2</span>
            <X class="h-4 w-4 text-muted-foreground ml-auto" />
          </div>
        </div>
      </div>

      <!-- Search Results -->
      <div class="space-y-3">
        <h3 class="text-sm font-semibold text-foreground">Hasil Pencarian</h3>
        
        <div class="bg-card border border-border rounded-lg p-4 hover:bg-accent/50 transition-colors cursor-pointer">
          <div class="flex items-start gap-3">
            <div class="w-12 h-12 bg-primary/10 rounded-lg flex items-center justify-center flex-shrink-0">
              <FileText class="h-6 w-6 text-primary" />
            </div>
            <div class="flex-1 min-w-0">
              <div class="font-medium text-foreground">Hasil Pencarian 1</div>
              <div class="text-sm text-muted-foreground line-clamp-2">
                Deskripsi singkat dari hasil pencarian yang menjelaskan konten yang ditemukan...
              </div>
              <div class="text-xs text-muted-foreground mt-1">2 menit yang lalu</div>
            </div>
          </div>
        </div>

        <div class="bg-card border border-border rounded-lg p-4 hover:bg-accent/50 transition-colors cursor-pointer">
          <div class="flex items-start gap-3">
            <div class="w-12 h-12 bg-green-100 rounded-lg flex items-center justify-center flex-shrink-0">
              <Image class="h-6 w-6 text-green-600" />
            </div>
            <div class="flex-1 min-w-0">
              <div class="font-medium text-foreground">Hasil Pencarian 2</div>
              <div class="text-sm text-muted-foreground line-clamp-2">
                Deskripsi singkat dari hasil pencarian yang menjelaskan konten yang ditemukan...
              </div>
              <div class="text-xs text-muted-foreground mt-1">5 menit yang lalu</div>
            </div>
          </div>
        </div>

        <div class="bg-card border border-border rounded-lg p-4 hover:bg-accent/50 transition-colors cursor-pointer">
          <div class="flex items-start gap-3">
            <div class="w-12 h-12 bg-purple-100 rounded-lg flex items-center justify-center flex-shrink-0">
              <Video class="h-6 w-6 text-purple-600" />
            </div>
            <div class="flex-1 min-w-0">
              <div class="font-medium text-foreground">Hasil Pencarian 3</div>
              <div class="text-sm text-muted-foreground line-clamp-2">
                Deskripsi singkat dari hasil pencarian yang menjelaskan konten yang ditemukan...
              </div>
              <div class="text-xs text-muted-foreground mt-1">10 menit yang lalu</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { Search, Clock, X, FileText, Image, Video } from 'lucide-vue-next'

useHead({
  title: 'Pencarian - Mobile App'
})
</script>