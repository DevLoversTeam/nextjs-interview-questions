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

<details>
<summary>2. Чим Next.js відрізняється від Create React App?</summary>

#### Next.js

**Create React App (CRA)** — це інструмент для швидкого створення клієнтського
React-застосунку (SPA), тоді як **Next.js** — **повноцінний React-фреймворк**,
орієнтований на продакшен і fullstack-розробку.

**Ключові відмінності:**

1. Рендеринг

- **CRA**:

  - лише **Client-Side Rendering (CSR)**
  - HTML генерується в браузері
  - гірший SEO та повільніший first paint

- **Next.js**:

  - **Server Components (default)**
  - **SSR / SSG / ISR**
  - streaming та partial rendering
  - кращий SEO та продуктивність

2. Архітектура

- **CRA**:

  - тільки frontend
  - відсутній серверний шар
  - API та auth — зовнішні сервіси

- **Next.js**:

  - fullstack-фреймворк
  - Route Handlers, Server Actions, Middleware
  - безпечна робота з БД та секретами

3. Маршрутизація

- **CRA**:

  - ручне налаштування (`react-router`)
  - вся логіка на клієнті

- **Next.js**:

  - файлова маршрутизація (`app/`)
  - layouts, loading/error states
  - nested routing без додаткових бібліотек

4. Продуктивність та оптимізації

- **CRA**:

  - мінімальні оптимізації
  - налаштовуються вручну

- **Next.js**:

  - автоматичний code splitting
  - оптимізація зображень та шрифтів
  - менший JS-бандл завдяки Server Components

5. Статус проєкту

- **CRA**:

  - проєкт **deprecated**
  - не рекомендований для нових застосунків

- **Next.js**:

  - активно розвивається
  - стандарт де-факто для React у продакшені

6. Використання в реальних проєктах

- **CRA** підходить для:

  - навчальних або простих SPA
  - прототипів

- **Next.js** підходить для:

  - SEO-орієнтованих застосунків
  - складних UI з серверною логікою
  - масштабованих продуктів

**Коротко:**

- CRA — це клієнтський SPA-бутстрап, Next.js — fullstack-фреймворк
- Next.js підтримує серверний рендеринг та оптимізації з коробки
- Для нових продакшен-проєктів обирають Next.js

</details>

<details>
<summary>3. Яку команду використовують для створення нового застосунку Next.js?</summary>

#### Next.js

Для створення нового застосунку на **Next.js+** використовується офіційний
CLI-інструмент **`create-next-app`**.

**Найпоширеніша та рекомендована команда:**

```bash
npx create-next-app@latest
```

**Після запуску CLI запропонує інтерактивну конфігурацію, зокрема:**

- використання TypeScript
- App Router (`app/`) — рекомендовано
- ESLint
- Tailwind CSS
- alias для імпортів (`@/`)
- використання `src/` директорії

**Приклад створення проєкту з іменем:**

```bash
npx create-next-app@latest my-next-app
```

**Що створюється за замовчуванням (Next.js 16+)**

- структура з **App Router**
- `app/layout.tsx` — кореневий layout
- `app/page.tsx` — головна сторінка
- підтримка **React Server Components**
- готова продакшен-конфігурація

```txt
my-next-app/
 ├─ app/
 │   ├─ layout.tsx
 │   └─ page.tsx
 ├─ public/
 ├─ next.config.js
 └─ package.json
```

**Важливе зауваження**

- Create React App не використовується
- Pages Router не є стандартом для нових проєктів
- create-next-app одразу створює production-ready середовище

**Коротко:**

- Для створення Next.js застосунку використовують npx create-next-app@latest
- CLI автоматично налаштовує App Router і сучасний стек
- Це рекомендований і єдиний актуальний спосіб старту з Next.js 16+

</details>

<details>
<summary>4. Яка різниця між Next.js та звичайним React-застосунком?</summary>

#### Next.js

**Звичайний React-застосунок** (SPA) — це клієнтський UI-рівень, тоді як
**Next.js** — це **повноцінний React-фреймворк**, який вирішує типові
продакшен-проблеми на рівні архітектури.

1. Рендеринг

- **React SPA**:

  - лише **Client-Side Rendering (CSR)**
  - HTML формується в браузері
  - залежність від `useEffect` для data fetching

- **Next.js**:

  - **React Server Components (default)**
  - підтримка **SSR / SSG / ISR**
  - data fetching на сервері без `useEffect`
  - кращий SEO та швидший first load

2. Архітектурний підхід

- **React SPA**:

  - лише frontend
  - бекенд — окремий сервіс
  - немає серверної логіки в проєкті

- **Next.js**:

  - fullstack-фреймворк
  - Server Actions, Route Handlers, Middleware
  - безпечна робота з БД, токенами, секретами

3. Маршрутизація

- **React SPA**:

  - потребує сторонніх бібліотек (`react-router`)
  - маршрути описуються вручну

- **Next.js**:

  - файлова маршрутизація через `app/`
  - layouts, nested routes, loading/error стани
  - менше boilerplate-коду

4. Продуктивність

- **React SPA**:

  - великий JS-бандл
  - рендеринг повністю на клієнті

- **Next.js**:

  - автоматичний code splitting
  - менший JS-бандл завдяки Server Components
  - streaming та partial rendering

5. Налаштування та best practices

- **React SPA**:

  - архітектурні рішення — на розробнику
  - легко припуститися помилок

- **Next.js**:

  - opinionated фреймворк
  - вбудовані best practices
  - швидший старт для продакшену

**Коротко:**

- React SPA — це лише UI-рівень, Next.js — fullstack-фреймворк
- Next.js підтримує серверний рендеринг та сучасні оптимізації
- Для реальних продакшен-проєктів обирають Next.js

</details>
