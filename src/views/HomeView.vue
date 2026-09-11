<script setup>
import ProjectCard from '../components/ProjectCard.vue'
import { projects } from '../data/projects.js'

const stack = [
  'Vue 3', 'React', 'TypeScript', 'Node.js', 'Express',
  'PostgreSQL', 'Prisma', 'Supabase', 'Tailwind CSS', 'Docker',
]

const process = [
  { step: '01', title: 'Обсуждаем задачу', text: 'Разбираем, что должен уметь сайт или сервис, кто им пользуется и какой бюджет по срокам.' },
  { step: '02', title: 'Прототип и оценка', text: 'Согласовываем структуру, дизайн-направление и стоимость до начала разработки — без сюрпризов в конце.' },
  { step: '03', title: 'Разработка', text: 'Frontend, backend, база данных, интеграции — показываю прогресс на промежуточных этапах.' },
  { step: '04', title: 'Запуск и поддержка', text: 'Разворачиваю на хостинге, передаю доступы, при необходимости — дорабатываю после запуска.' },
]
</script>

<template>
  <div>
    <!-- Hero -->
    <section class="relative overflow-hidden">
      <div class="pointer-events-none absolute inset-0 bg-[radial-gradient(ellipse_60%_50%_at_50%_-10%,theme(colors.brand.500/15%),transparent)]" />
      <div class="relative mx-auto max-w-6xl px-6 pb-20 pt-20 sm:pt-28">
        <p class="text-sm font-medium text-brand-400">Full-stack веб-разработка</p>
        <h1 class="mt-4 max-w-3xl text-4xl font-semibold leading-tight text-ink-50 sm:text-5xl">
          Делаю сайты и веб-сервисы, которые реально работают —
          <span class="text-ink-400">с базой данных, бронированием и админ-панелью.</span>
        </h1>
        <p class="mt-6 max-w-xl text-lg text-ink-400">
          Ниже — не макеты, а рабочие демо-версии моих проектов. Открывайте, кликайте,
          пробуйте записаться или оформить заказ — так же, как будет у ваших клиентов.
        </p>
        <div class="mt-8 flex flex-wrap gap-4">
          <a href="#work" class="rounded-full bg-brand-500 px-6 py-3 text-sm font-medium text-ink-950 transition hover:bg-brand-400">
            Смотреть проекты
          </a>
          <a href="#contact" class="rounded-full border border-white/10 px-6 py-3 text-sm font-medium text-ink-100 transition hover:border-white/30">
            Обсудить задачу
          </a>
        </div>
      </div>
    </section>

    <!-- Work -->
    <section id="work" class="mx-auto max-w-6xl px-6 py-16 scroll-mt-20">
      <div class="mb-10 flex items-end justify-between">
        <div>
          <p class="text-sm font-medium text-brand-400">Проекты</p>
          <h2 class="mt-2 text-2xl font-semibold text-ink-50 sm:text-3xl">Реальные кейсы для клиентов</h2>
        </div>
      </div>

      <div class="grid gap-6 sm:grid-cols-2">
        <ProjectCard v-for="p in projects" :key="p.slug" :project="p" />
      </div>
    </section>

    <!-- About / stack -->
    <section id="about" class="border-t border-white/5 bg-ink-900/40 scroll-mt-20">
      <div class="mx-auto max-w-6xl px-6 py-16">
        <p class="text-sm font-medium text-brand-400">Обо мне</p>
        <h2 class="mt-2 max-w-2xl text-2xl font-semibold text-ink-50 sm:text-3xl">
          Делаю сайты и веб-приложения под ключ — от лендинга до системы с базой данных
        </h2>
        <p class="mt-4 max-w-2xl text-ink-400">
          Беру проект от идеи до запуска: проектирую структуру, пишу frontend и backend,
          настраиваю базу данных и хостинг. Не только "красивый фронт" — сайт реально
          работает: принимает заявки, хранит данные, показывает их в админ-панели.
        </p>

        <div class="mt-8 flex flex-wrap gap-2">
          <span
            v-for="s in stack"
            :key="s"
            class="rounded-full border border-white/10 bg-ink-950 px-3 py-1.5 text-sm text-ink-300"
          >
            {{ s }}
          </span>
        </div>
      </div>
    </section>

    <!-- Process -->
    <section class="mx-auto max-w-6xl px-6 py-16">
      <p class="text-sm font-medium text-brand-400">Как я работаю</p>
      <h2 class="mt-2 text-2xl font-semibold text-ink-50 sm:text-3xl">От заявки до запуска</h2>

      <div class="mt-10 grid gap-8 sm:grid-cols-2 lg:grid-cols-4">
        <div v-for="p in process" :key="p.step">
          <span class="text-sm font-mono text-ink-600">{{ p.step }}</span>
          <h3 class="mt-2 font-semibold text-ink-50">{{ p.title }}</h3>
          <p class="mt-2 text-sm text-ink-400">{{ p.text }}</p>
        </div>
      </div>
    </section>
  </div>
</template>
