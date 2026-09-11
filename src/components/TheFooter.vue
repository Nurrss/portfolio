<script setup>
const year = new Date().getFullYear()
</script>

<template>
  <footer id="contact" class="border-t border-white/5 bg-ink-950">
    <div class="mx-auto max-w-6xl px-6 py-16">
      <div class="flex flex-col items-start justify-between gap-8 border-b border-white/5 pb-12 md:flex-row md:items-end">
        <div>
          <p class="text-sm font-medium text-brand-400">Есть задача?</p>
          <h2 class="mt-3 max-w-md text-3xl font-semibold text-ink-50 sm:text-4xl">
            Обсудим ваш проект и посчитаем сроки
          </h2>
        </div>
        <a
          href="mailto:nurrs.serkul@gmail.com"
          class="inline-flex items-center gap-2 rounded-full bg-brand-500 px-6 py-3 text-sm font-medium text-ink-950 transition hover:bg-brand-400"
        >
          Написать на почту
        </a>
      </div>

      <div class="flex flex-col gap-4 pt-8 text-sm text-ink-400 sm:flex-row sm:items-center sm:justify-between">
        <p>© {{ year }} Nursultan. Все проекты — реальные заказы, показаны с согласия на демонстрацию.</p>
        <a href="mailto:nurrs.serkul@gmail.com" class="text-ink-300 transition hover:text-brand-400">
          nurrs.serkul@gmail.com
        </a>
      </div>
    </div>
  </footer>
</template>
