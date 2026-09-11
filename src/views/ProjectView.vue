<script setup>
import { computed } from 'vue'
import { useRoute, RouterLink } from 'vue-router'
import { getProject, projects } from '../data/projects.js'

const route = useRoute()
const project = computed(() => getProject(route.params.slug))

const otherProjects = computed(() =>
  projects.filter((p) => p.slug !== route.params.slug).slice(0, 2)
)

const accentButton = {
  rose: 'bg-rose-500 hover:bg-rose-400 text-ink-950',
  sky: 'bg-sky-500 hover:bg-sky-400 text-ink-950',
  violet: 'bg-violet-500 hover:bg-violet-400 text-ink-950',
  amber: 'bg-amber-500 hover:bg-amber-400 text-ink-950',
}
</script>

<template>
  <div v-if="project" class="mx-auto max-w-4xl px-6 py-16">
    <RouterLink to="/#work" class="inline-flex items-center gap-1 text-sm text-ink-400 hover:text-ink-100">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M19 12H5M11 18l-6-6 6-6" /></svg>
      Все проекты
    </RouterLink>

    <div class="mt-6">
      <h1 class="text-3xl font-semibold text-ink-50 sm:text-4xl">{{ project.title }}</h1>
      <p class="mt-3 text-lg text-ink-400">{{ project.tagline }}</p>
    </div>

    <div class="mt-8 flex flex-wrap items-center gap-3">
      <a
        v-if="project.demoUrl"
        :href="project.demoUrl"
        target="_blank"
        rel="noopener"
        class="inline-flex items-center gap-2 rounded-full px-6 py-3 text-sm font-medium transition"
        :class="accentButton[project.accent]"
      >
        Открыть демо
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M7 17L17 7M7 7h10v10" /></svg>
      </a>
      <span v-else class="inline-flex items-center gap-2 rounded-full border border-white/10 px-6 py-3 text-sm text-ink-400">
        Демо готовится — напишите мне, покажу вживую
      </span>
      <span v-if="project.demoNote" class="text-sm text-ink-500">{{ project.demoNote }}</span>
    </div>

    <img
      v-if="project.cover"
      :src="project.cover"
      :alt="project.title"
      class="mt-10 w-full rounded-2xl border border-white/5 object-cover"
    />

    <div class="mt-12 grid gap-10 sm:grid-cols-2">
      <div>
        <h2 class="text-sm font-medium text-brand-400">Задача</h2>
        <p class="mt-2 text-ink-300">{{ project.problem }}</p>
      </div>
      <div>
        <h2 class="text-sm font-medium text-brand-400">Решение</h2>
        <p class="mt-2 text-ink-300">{{ project.solution }}</p>
      </div>
    </div>

    <div class="mt-12">
      <h2 class="text-sm font-medium text-brand-400">Что реализовано</h2>
      <ul class="mt-3 grid gap-2 sm:grid-cols-2">
        <li v-for="f in project.features" :key="f" class="flex items-start gap-2 text-ink-300">
          <svg class="mt-1 shrink-0" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" /></svg>
          {{ f }}
        </li>
      </ul>
    </div>

    <div class="mt-12 grid gap-10 sm:grid-cols-2">
      <div>
        <h2 class="text-sm font-medium text-brand-400">Технологии</h2>
        <div class="mt-3 flex flex-wrap gap-2">
          <span v-for="t in project.stack" :key="t" class="rounded-full border border-white/10 bg-ink-900 px-3 py-1 text-sm text-ink-300">
            {{ t }}
          </span>
        </div>
      </div>
      <div>
        <h2 class="text-sm font-medium text-brand-400">Моя роль</h2>
        <p class="mt-2 text-ink-300">{{ project.role }}</p>
      </div>
    </div>

    <div class="mt-16 border-t border-white/5 pt-10">
      <p class="text-sm font-medium text-brand-400">Другие проекты</p>
      <div class="mt-6 grid gap-4 sm:grid-cols-2">
        <RouterLink
          v-for="p in otherProjects"
          :key="p.slug"
          :to="`/projects/${p.slug}`"
          class="rounded-xl border border-white/5 bg-ink-900 p-5 transition hover:border-white/10 hover:bg-ink-800"
        >
          <h3 class="font-semibold text-ink-50">{{ p.title }}</h3>
          <p class="mt-1 text-sm text-ink-400">{{ p.tagline }}</p>
        </RouterLink>
      </div>
    </div>
  </div>

  <div v-else class="mx-auto max-w-4xl px-6 py-24 text-center text-ink-400">
    Проект не найден.
    <RouterLink to="/" class="text-brand-400 underline">На главную</RouterLink>
  </div>
</template>
