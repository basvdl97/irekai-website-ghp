<template>
  <div class="app-root grid-bg">
    <NavBar />
    <main>
      <RouterView v-slot="{ Component }">
        <Transition name="page" mode="out-in">
          <component :is="Component" :key="$route.path" />
        </Transition>
      </RouterView>
    </main>
    <SiteFooter />
  </div>
</template>

<script setup>
import NavBar    from '@/components/NavBar.vue'
import SiteFooter from '@/components/SiteFooter.vue'
</script>

<style scoped>
.app-root {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
main { flex: 1; }
</style>
