<script setup>
defineProps({
  project: { type: Object, required: true },
})

const accentGradient = {
  rose: 'from-rose-500/30 via-rose-500/5 to-transparent',
  sky: 'from-sky-500/30 via-sky-500/5 to-transparent',
  violet: 'from-violet-500/30 via-violet-500/5 to-transparent',
  amber: 'from-amber-500/30 via-amber-500/5 to-transparent',
}

const accentText = {
  rose: 'text-rose-300',
  sky: 'text-sky-300',
  violet: 'text-violet-300',
  amber: 'text-amber-300',
}
</script>

<template>
  <RouterLink
    :to="`/projects/${project.slug}`"
    class="group flex flex-col overflow-hidden rounded-2xl border border-white/5 bg-ink-900 transition hover:border-white/10 hover:bg-ink-800"
  >
    <div
      class="relative flex aspect-[16/10] items-center justify-center overflow-hidden bg-gradient-to-br"
      :class="accentGradient[project.accent]"
    >
      <img
        v-if="project.cover"
        :src="project.cover"
        :alt="project.title"
        class="h-full w-full object-cover object-top transition duration-300 group-hover:scale-[1.02]"
      />
      <span v-else class="text-2xl font-semibold text-ink-100/80">{{ project.title }}</span>
    </div>

    <div class="flex flex-1 flex-col gap-3 p-6">
      <div>
        <h3 class="text-lg font-semibold text-ink-50">{{ project.title }}</h3>
        <p class="mt-1 text-sm text-ink-400">{{ project.tagline }}</p>
      </div>

      <ul class="mt-auto flex flex-wrap gap-x-3 gap-y-1 pt-2 text-xs text-ink-500">
        <li v-for="t in project.stack.slice(0, 4)" :key="t">{{ t }}</li>
      </ul>

      <span class="inline-flex items-center gap-1 text-sm font-medium" :class="accentText[project.accent]">
        Смотреть кейс
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="transition group-hover:translate-x-0.5">
          <path stroke-linecap="round" stroke-linejoin="round" d="M5 12h14M13 6l6 6-6 6" />
        </svg>
      </span>
    </div>
  </RouterLink>
</template>
