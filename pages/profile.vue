<template>
  <div class="min-h-screen p-4">
    <div class="max-w-md mx-auto">
      <!-- Header -->
      <div class="mb-6">
        <h1 class="text-2xl font-bold text-foreground mb-2">Profil</h1>
        <p class="text-muted-foreground">Informasi akun Anda</p>
      </div>

      <!-- Profile Card -->
      <div class="bg-gradient-to-r from-primary/10 to-purple-500/10 border border-primary/20 rounded-lg p-6 mb-6">
        <div class="flex items-center gap-4 mb-4">
          <div class="w-20 h-20 bg-primary rounded-full flex items-center justify-center relative">
            <User class="h-10 w-10 text-primary-foreground" />
            <div class="absolute -bottom-1 -right-1 w-6 h-6 bg-green-500 rounded-full border-2 border-background"></div>
          </div>
          <div>
            <h2 class="text-xl font-semibold text-foreground">John Doe</h2>
            <p class="text-muted-foreground">john.doe@example.com</p>
            <div class="flex items-center gap-2 mt-1">
              <Crown class="h-4 w-4 text-yellow-500" />
              <span class="text-sm text-yellow-600 font-medium">Premium Member</span>
            </div>
          </div>
        </div>
        <button class="w-full py-2 bg-primary text-primary-foreground rounded-lg font-medium hover:bg-primary/90 transition-colors">
          Edit Profil
        </button>
      </div>

      <!-- Stats -->
      <div class="grid grid-cols-3 gap-4 mb-6">
        <div class="bg-card border border-border rounded-lg p-4 text-center">
          <div class="text-2xl font-bold text-primary">24</div>
          <div class="text-xs text-muted-foreground">Posts</div>
        </div>
        <div class="bg-card border border-border rounded-lg p-4 text-center">
          <div class="text-2xl font-bold text-green-600">156</div>
          <div class="text-xs text-muted-foreground">Followers</div>
        </div>
        <div class="bg-card border border-border rounded-lg p-4 text-center">
          <div class="text-2xl font-bold text-purple-600">89</div>
          <div class="text-xs text-muted-foreground">Following</div>
        </div>
      </div>

      <!-- Quick Actions -->
      <div class="space-y-2 mb-6">
        <div class="bg-card border border-border rounded-lg p-4 flex items-center justify-between hover:bg-accent/50 transition-colors cursor-pointer">
          <div class="flex items-center gap-3">
            <div class="w-10 h-10 bg-blue-100 rounded-lg flex items-center justify-center">
              <UserCircle class="h-5 w-5 text-blue-600" />
            </div>
            <div>
              <div class="font-medium">Informasi Personal</div>
              <div class="text-sm text-muted-foreground">Kelola data pribadi</div>
            </div>
          </div>
          <ChevronRight class="h-4 w-4 text-muted-foreground" />
        </div>

        <div class="bg-card border border-border rounded-lg p-4 flex items-center justify-between hover:bg-accent/50 transition-colors cursor-pointer">
          <div class="flex items-center gap-3">
            <div class="w-10 h-10 bg-green-100 rounded-lg flex items-center justify-center">
              <Shield class="h-5 w-5 text-green-600" />
            </div>
            <div>
              <div class="font-medium">Keamanan & Privasi</div>
              <div class="text-sm text-muted-foreground">Password & autentikasi</div>
            </div>
          </div>
          <ChevronRight class="h-4 w-4 text-muted-foreground" />
        </div>

        <div class="bg-card border border-border rounded-lg p-4 flex items-center justify-between hover:bg-accent/50 transition-colors cursor-pointer">
          <div class="flex items-center gap-3">
            <div class="w-10 h-10 bg-purple-100 rounded-lg flex items-center justify-center">
              <Bell class="h-5 w-5 text-purple-600" />
            </div>
            <div>
              <div class="font-medium">Notifikasi</div>
              <div class="text-sm text-muted-foreground">Atur preferensi notifikasi</div>
            </div>
          </div>
          <ChevronRight class="h-4 w-4 text-muted-foreground" />
        </div>

        <div class="bg-card border border-border rounded-lg p-4 flex items-center justify-between hover:bg-accent/50 transition-colors cursor-pointer">
          <div class="flex items-center gap-3">
            <div class="w-10 h-10 bg-orange-100 rounded-lg flex items-center justify-center">
              <CreditCard class="h-5 w-5 text-orange-600" />
            </div>
            <div>
              <div class="font-medium">Billing & Subscription</div>
              <div class="text-sm text-muted-foreground">Kelola pembayaran</div>
            </div>
          </div>
          <ChevronRight class="h-4 w-4 text-muted-foreground" />
        </div>
      </div>

      <!-- Achievement Section -->
      <div class="bg-card border border-border rounded-lg p-4 mb-6">
        <h3 class="font-semibold mb-3 flex items-center gap-2">
          <Award class="h-4 w-4 text-yellow-500" />
          Pencapaian Terbaru
        </h3>
        <div class="space-y-3">
          <div class="flex items-center gap-3">
            <div class="w-8 h-8 bg-yellow-100 rounded-full flex items-center justify-center">
              <Medal class="h-4 w-4 text-yellow-600" />
            </div>
            <div class="flex-1">
              <div class="text-sm font-medium">First Post Achievement</div>
              <div class="text-xs text-muted-foreground">Berhasil membuat post pertama</div>
            </div>
            <div class="text-xs text-muted-foreground">2 hari lalu</div>
          </div>
          
          <div class="flex items-center gap-3">
            <div class="w-8 h-8 bg-green-100 rounded-full flex items-center justify-center">
              <Target class="h-4 w-4 text-green-600" />
            </div>
            <div class="flex-1">
              <div class="text-sm font-medium">Active User</div>
              <div class="text-xs text-muted-foreground">Login 7 hari berturut-turut</div>
            </div>
            <div class="text-xs text-muted-foreground">1 minggu lalu</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { 
  User, 
  Crown, 
  ChevronRight, 
  Shield, 
  Bell, 
  UserCircle, 
  CreditCard, 
  Award, 
  Medal, 
  Target 
} from 'lucide-vue-next'

useHead({
  title: 'Profil - Mobile App'
})
</script>