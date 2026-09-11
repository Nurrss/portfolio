<script setup>
import { ref } from 'vue'

const open = ref(false)
const links = [
  { href: '/#work', label: 'Проекты' },
  { href: '/#about', label: 'Обо мне' },
  { href: '/#contact', label: 'Контакты' },
]
</script>

<template>
  <header class="sticky top-0 z-40 border-b border-white/5 bg-ink-950/80 backdrop-blur">
    <div class="mx-auto flex max-w-6xl items-center justify-between px-6 py-4">
      <RouterLink to="/" class="text-sm font-semibold tracking-wide text-ink-50">
        Nursultan<span class="text-brand-400">.dev</span>
      </RouterLink>

      <nav class="hidden items-center gap-8 text-sm text-ink-300 md:flex">
        <a v-for="l in links" :key="l.href" :href="l.href" class="transition hover:text-ink-50">
          {{ l.label }}
        </a>
      </nav>

      <a
        href="/#contact"
        class="hidden rounded-full bg-brand-500 px-4 py-2 text-sm font-medium text-ink-950 transition hover:bg-brand-400 md:inline-block"
      >
        Обсудить проект
      </a>

      <button
        class="text-ink-100 md:hidden"
        aria-label="Меню"
        @click="open = !open"
      >
        <svg v-if="!open" width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path stroke-linecap="round" d="M4 7h16M4 12h16M4 17h16"/></svg>
        <svg v-else width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path stroke-linecap="round" d="M6 6l12 12M18 6L6 18"/></svg>
      </button>
    </div>

    <div v-if="open" class="border-t border-white/5 px-6 py-4 md:hidden">
      <nav class="flex flex-col gap-4 text-sm text-ink-300">
        <a v-for="l in links" :key="l.href" :href="l.href" class="hover:text-ink-50" @click="open = false">
          {{ l.label }}
        </a>
        <a href="/#contact" class="font-medium text-brand-400" @click="open = false">Обсудить проект</a>
      </nav>
    </div>
  </header>
</template>
