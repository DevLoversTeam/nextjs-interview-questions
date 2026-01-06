<h1>
  Next.js <img src="./assets/nextjs.svg" width="40" height="40" />
</h1>

<h2>Найпопулярніші запитання та відповіді на співбесіді з Next.js</h2>

<details>
<summary>1. Що таке Next.js і які його основні можливості?</summary>

#### Next.js

**Next.js** — це **React-фреймворк для продакшену**, який розширює можливості
React та вирішує типові проблеми SPA, такі як SEO, продуктивність, маршрутизація
та робота з сервером.

Починаючи з **Next.js 13+**, основним підходом є **App Router**, який у
**Next.js 16+** є стандартом для розробки.

**Основні можливості Next.js:**

1. Гібридний рендеринг

**Next.js підтримує кілька стратегій рендерингу в межах одного застосунку:**

- **Server Components (default)** — виконуються на сервері
- **Server-Side Rendering (SSR)**
- **Static Site Generation (SSG)**
- **Incremental Static Regeneration (ISR)**

Це дозволяє оптимально балансувати між продуктивністю та динамічністю.

2. App Router та файлова маршрутизація

**Маршрути створюються на основі структури папок у `app/`:**

```txt
app/
 ├─ page.tsx        // /
 ├─ blog/
 │   └─ page.tsx    // /blog
 └─ layout.tsx      // спільний layout
```

**Підтримуються:**

- вкладені layouts
- loading / error states
- route segments
- middleware

3. React Server Components

**За замовчуванням компоненти є серверними, що дозволяє:**

- зменшити розмір JS-бандла
- безпечно працювати з БД та секретами
- виконувати data fetching без useEffect

```TypeScript
export default async function Page() {
  const data = await fetch('https://api.example.com/data').then(res => res.json());

  return <pre>{JSON.stringify(data, null, 2)}</pre>;
}
```

4. Вбудований data fetching

**Next.js інтегрує fetch з контролем кешування та revalidation:**

```TypeScript
await fetch(url, { cache: 'no-store' });      // SSR
await fetch(url, { next: { revalidate: 60 } }); // ISR
```

5. Оптимізації з коробки

**Next.js надає вбудовані оптимізації:**

- автоматичний code splitting
- оптимізація зображень (next/image)
- оптимізація шрифтів (next/font)
- streaming та partial rendering

6. Fullstack можливості

**Next.js дозволяє будувати fullstack-застосунки:**

- Route Handlers (app/api)
- Server Actions
- Middleware
- інтеграція з базами даних та auth

**Коротко:**

- Next.js — це production-ready React-фреймворк
- App Router та Server Components — основа сучасного Next.js
- Забезпечує високу продуктивність, SEO та масштабованість

</details>
