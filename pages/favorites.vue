<template>
  <div class="min-h-screen p-4">
    <div class="max-w-md mx-auto">
      <!-- Header -->
      <div class="mb-6">
        <h1 class="text-2xl font-bold text-foreground mb-2">Favorit</h1>
        <p class="text-muted-foreground">Item yang Anda sukai</p>
      </div>

      <!-- Filter Tabs -->
      <div class="flex gap-1 mb-6 bg-muted p-1 rounded-lg">
        <button class="flex-1 py-2 px-3 bg-background text-foreground rounded-md text-sm font-medium shadow-sm">
          Semua
        </button>
        <button class="flex-1 py-2 px-3 text-muted-foreground rounded-md text-sm font-medium hover:text-foreground transition-colors">
          Terbaru
        </button>
        <button class="flex-1 py-2 px-3 text-muted-foreground rounded-md text-sm font-medium hover:text-foreground transition-colors">
          Populer
        </button>
      </div>

      <!-- Stats Overview -->
      <div class="bg-gradient-to-r from-primary/10 to-purple-500/10 border border-primary/20 rounded-lg p-4 mb-6">
        <div class="flex items-center gap-3">
          <Heart class="h-8 w-8 text-red-500 fill-current" />
          <div>
            <div class="text-2xl font-bold text-foreground">12</div>
            <div class="text-sm text-muted-foreground">Total Favorit</div>
          </div>
        </div>
      </div>

      <!-- Favorites List -->
      <div class="space-y-3">
        <div class="bg-card border border-border rounded-lg p-4 hover:bg-accent/50 transition-colors">
          <div class="flex items-start gap-3">
            <div class="w-16 h-16 bg-gradient-to-br from-blue-400 to-blue-600 rounded-lg flex items-center justify-center flex-shrink-0">
              <Star class="h-8 w-8 text-white" />
            </div>
            <div class="flex-1 min-w-0">
              <div class="flex items-start justify-between">
                <div>
                  <div class="font-medium text-foreground">Item Favorit 1</div>
                  <div class="text-sm text-muted-foreground">Kategori: Design</div>
                  <div class="text-xs text-muted-foreground mt-1">Ditambahkan kemarin</div>
                </div>
                <button class="p-1 hover:bg-accent rounded-md transition-colors">
                  <Heart class="h-5 w-5 text-red-500 fill-current" />
                </button>
              </div>
              <div class="flex items-center gap-2 mt-3">
                <div class="text-xs bg-blue-100 text-blue-700 px-2 py-1 rounded-full">Premium</div>
                <div class="text-xs bg-green-100 text-green-700 px-2 py-1 rounded-full">Trending</div>
              </div>
            </div>
          </div>
        </div>
        
        <div class="bg-card border border-border rounded-lg p-4 hover:bg-accent/50 transition-colors">
          <div class="flex items-start gap-3">
            <div class="w-16 h-16 bg-gradient-to-br from-green-400 to-green-600 rounded-lg flex items-center justify-center flex-shrink-0">
              <Bookmark class="h-8 w-8 text-white" />
            </div>
            <div class="flex-1 min-w-0">
              <div class="flex items-start justify-between">
                <div>
                  <div class="font-medium text-foreground">Item Favorit 2</div>
                  <div class="text-sm text-muted-foreground">Kategori: Development</div>
                  <div class="text-xs text-muted-foreground mt-1">Ditambahkan minggu lalu</div>
                </div>
                <button class="p-1 hover:bg-accent rounded-md transition-colors">
                  <Heart class="h-5 w-5 text-red-500 fill-current" />
                </button>
              </div>
              <div class="flex items-center gap-2 mt-3">
                <div class="text-xs bg-purple-100 text-purple-700 px-2 py-1 rounded-full">New</div>
                <div class="text-xs bg-orange-100 text-orange-700 px-2 py-1 rounded-full">Popular</div>
              </div>
            </div>
          </div>
        </div>

        <div class="bg-card border border-border rounded-lg p-4 hover:bg-accent/50 transition-colors">
          <div class="flex items-start gap-3">
            <div class="w-16 h-16 bg-gradient-to-br from-purple-400 to-purple-600 rounded-lg flex items-center justify-center flex-shrink-0">
              <Trophy class="h-8 w-8 text-white" />
            </div>
            <div class="flex-1 min-w-0">
              <div class="flex items-start justify-between">
                <div>
                  <div class="font-medium text-foreground">Item Favorit 3</div>
                  <div class="text-sm text-muted-foreground">Kategori: Business</div>
                  <div class="text-xs text-muted-foreground mt-1">Ditambahkan bulan lalu</div>
                </div>
                <button class="p-1 hover:bg-accent rounded-md transition-colors">
                  <Heart class="h-5 w-5 text-red-500 fill-current" />
                </button>
              </div>
              <div class="flex items-center gap-2 mt-3">
                <div class="text-xs bg-yellow-100 text-yellow-700 px-2 py-1 rounded-full">Featured</div>
              </div>
            </div>
          </div>
        </div>

        <div class="bg-card border border-border rounded-lg p-4 hover:bg-accent/50 transition-colors">
          <div class="flex items-start gap-3">
            <div class="w-16 h-16 bg-gradient-to-br from-red-400 to-red-600 rounded-lg flex items-center justify-center flex-shrink-0">
              <Gift class="h-8 w-8 text-white" />
            </div>
            <div class="flex-1 min-w-0">
              <div class="flex items-start justify-between">
                <div>
                  <div class="font-medium text-foreground">Item Favorit 4</div>
                  <div class="text-sm text-muted-foreground">Kategori: Lifestyle</div>
                  <div class="text-xs text-muted-foreground mt-1">Ditambahkan 2 bulan lalu</div>
                </div>
                <button class="p-1 hover:bg-accent rounded-md transition-colors">
                  <Heart class="h-5 w-5 text-red-500 fill-current" />
                </button>
              </div>
              <div class="flex items-center gap-2 mt-3">
                <div class="text-xs bg-red-100 text-red-700 px-2 py-1 rounded-full">Limited</div>
                <div class="text-xs bg-gray-100 text-gray-700 px-2 py-1 rounded-full">Classic</div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Load More Button -->
      <div class="mt-6 text-center">
        <button class="w-full py-3 text-primary font-medium hover:bg-primary/10 rounded-lg transition-colors">
          Muat Lebih Banyak
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { Heart, Star, Bookmark, Trophy, Gift } from 'lucide-vue-next'

useHead({
  title: 'Favorit - Mobile App'
})
</script>