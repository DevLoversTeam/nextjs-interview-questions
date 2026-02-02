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

<details>
<summary>5. Які задачі Next.js вирішує на рівні фронтенду і бекенду?</summary>

#### Next.js

**Next.js** позиціонується як **fullstack React-фреймворк**, оскільки закриває
як типові фронтенд-задачі, так і значну частину серверної логіки без потреби в
окремому бекенд-проєкті.

#### Задачі, які Next.js вирішує на рівні фронтенду

1. Маршрутизація та навігація

- файлова маршрутизація через `app/`
- вкладені маршрути та layouts
- loading / error стани
- клієнтська навігація без перезавантаження сторінки

```txt
app/
 ├─ layout.tsx
 ├─ page.tsx
 └─ dashboard/
     └─ page.tsx
```

2. Рендеринг та продуктивність

- React Server Components за замовчуванням
- SSR / SSG / ISR
- streaming та partial rendering
- зменшення JS-бандла

3. Оптимізації з коробки

- оптимізація зображень (`next/image`)
- оптимізація шрифтів (`next/font`)
- автоматичний code splitting
- prefetch навігації

4. Керування UI-станами

- loading (`loading.tsx`)
- error boundaries (`error.tsx`)
- not found (`not-found.tsx`)
- metadata для SEO

#### Задачі, які Next.js вирішує на рівні бекенду

1. Data fetching на сервері

- виконання запитів до API або БД на сервері
- кешування та revalidation через fetch

```TypeScript
await fetch(url, { next: { revalidate: 60 } });
```

2. API та серверна логіка

- **Route Handlers** (`app/api/*`)
- побудова REST або edge-ендпоінтів
- робота без окремого Express / Nest сервера

```TypeScript
// app/api/users/route.ts
export async function GET() {
  return Response.json({ users: [] });
}
```

3. Server Actions

- виклик серверної логіки напряму з компонентів
- обробка форм без клієнтського API

```TypeScript
'use server';

export async function createUser(formData: FormData) {
  // серверна логіка
}
```

4. Middleware

- перевірка авторизації
- редиректи
- геолокація
- A/B логіка

```TypeScript
export function middleware(req: Request) {
  // auth, redirects, headers
}
```

5. Безпека

- доступ до секретів лише на сервері
- відсутність витоку токенів у браузер
- контроль доступу на рівні маршруту

**Коротко:**

- Next.js закриває фронтенд-задачі: UI, маршрути, оптимізації, SEO
- На бекенді: data fetching, API, server actions, middleware
- Це дозволяє будувати повноцінні fullstack-застосунки в одному проєкті

</details>

<details>
<summary>6. Як Next.js обробляє серверний рендеринг (SSR)?</summary>

#### Next.js

У **Next.js 16+** серверний рендеринг є частиною **єдиного гібридного підходу**,
побудованого навколо **React Server Components** та **App Router**.  
SSR означає, що HTML сторінки **генерується на сервері при кожному запиті**, а
не під час білду.

#### Як працює SSR у Next.js 16+

1. **Запит від користувача** надходить на сервер
2. **Server Components** виконуються на сервері
3. Дані отримуються під час рендерингу
4. Сервер повертає готовий HTML
5. На клієнті відбувається гідратація Client Components

#### Як увімкнути SSR в App Router

У Next.js 16+ **SSR не вмикається явно** — він визначається через **налаштування
кешування**.

SSR через `fetch` з `no-store`

```TypeScript
export default async function Page() {
  const data = await fetch('https://api.example.com/data', {
    cache: 'no-store',
  }).then(res => res.json());

  return <pre>{JSON.stringify(data, null, 2)}</pre>;
}
```

- `cache: 'no-store'` → сторінка рендериться на кожен запит
- дані не кешуються
- класичний SSR

#### Динамічні сторінки (force-dynamic)

SSR також активується, якщо сторінка є динамічною:

```TypeScript
export const dynamic = 'force-dynamic';
```

**Або якщо використовується:**

- cookies
- headers
- auth-сесії
- персоналізовані дані

#### Коли використовувати SSR

**SSR доцільний, якщо:**

- дані часто змінюються
- контент персоналізований
- потрібна актуальність у реальному часі
- залежність від cookies / headers / auth

**Приклади:**

- dashboard
- профіль користувача
- admin-панель

#### SSR vs інші стратегії

**SSR** — рендер на кожен запит **SSG** — рендер під час білду **ISR** —
статичний рендер + revalidation **RSC** — базовий механізм виконання на сервері

У Next.js 16+ SSR — це не окремий режим, а частина гібридної моделі.

**Важливо**

- `getServerSideProps` не використовується (Pages Router)
- SSR у App Router керується через cache та dynamic
- `useEffect` не потрібен для data fetching

**Коротко:**

- SSR у Next.js 16+ виконується на сервері при кожному запиті
- Вмикається через cache: `'no-store'` або динамічний рендеринг
- Є частиною гібридної моделі App Router та Server Components

</details>

<details>
<summary>7. У Next.js як зробити так, щоб сторінка рендерилась на сервері при кожному запиті?</summary>

#### Next.js

У **Next.js 16+** сторінка рендериться **на сервері при кожному запиті (SSR)**
не через окремий режим, а **через керування кешуванням і динамічністю**.

Існує кілька коректних способів це зробити.

1. Використати `fetch` з `cache: 'no-store'` (рекомендовано)

Це **основний і найпоширеніший спосіб** увімкнути SSR у App Router.

```TypeScript
export default async function Page() {
  const data = await fetch('https://api.example.com/data', {
    cache: 'no-store',
  }).then(res => res.json());

  return <div>{data.title}</div>;
}
```

- сторінка рендериться на кожен запит
- дані не кешуються
- повноцінний SSR

2. Примусово зробити сторінку динамічною

Можна явно вказати, що сторінка має бути динамічною:

```TypeScript
export const dynamic = 'force-dynamic';
```

**Це означає:**

- рендер при кожному запиті
- навіть без fetch

3. Використання cookies або headers

**Якщо сторінка читає:**

- cookies()
- headers()
- дані користувача / сесії

→ Next.js автоматично вмикає SSR

```TypeScript
import { cookies } from 'next/headers';

export default function Page() {
  const token = cookies().get('token');
  return <div>{token?.value}</div>;
}
```

#### Що не потрібно робити

- `getServerSideProps` — Pages Router
- `useEffect` для SSR
- ручне керування сервером

#### Коли це доцільно

**SSR при кожному запиті використовують для:**

- персоналізованих сторінок
- dashboard
- admin-панелей
- контенту, що часто змінюється

**Коротко:**

SSR у Next.js 16+ вмикається через `cache: 'no-store'` Або через
`dynamic = 'force-dynamic'` Next.js автоматично рендерить сторінку на сервері,
якщо є cookies / headers

</details>

<details>
<summary>8. Що таке автоматична оптимізація сайтів у Next.js?</summary>

#### Next.js

**Автоматична оптимізація в Next.js** — це набір вбудованих механізмів, які
**покращують продуктивність, SEO та UX автоматично**, без ручної конфігурації.  
У **Next.js 16+ (App Router)** більшість оптимізацій працюють **“out of the
box”** і вважаються стандартною поведінкою фреймворку.

#### Основні види автоматичної оптимізації

1. Автоматичний вибір стратегії рендерингу

Next.js **сам визначає**, як рендерити сторінку:

- **Static (SSG)** — якщо дані кешуються
- **ISR** — якщо задано `revalidate`
- **SSR** — якщо `no-store`, cookies або headers
- **Server Components** — за замовчуванням

```TypeScript
await fetch(url, { next: { revalidate: 60 } }); // ISR
await fetch(url, { cache: 'no-store' });        // SSR
```

Розробнику не потрібно вручну обирати режим.

2. Automatic Code Splitting

**Next.js автоматично:**

- ділить код по маршрутах
- завантажує лише потрібний JS
- зменшує initial bundle

Це працює без налаштувань, на рівні App Router.

3. React Server Components (RSC)

- серверні компоненти не потрапляють у JS-бандл
- логіка та data fetching виконуються на сервері
- менше JavaScript у браузері

```TypeScript
export default async function Page() {
  const data = await getData();
  return <div>{data.title}</div>;
}
```

4. Оптимізація зображень (`next/image`)

- автоматичний lazy loading
- responsive images
- modern formats (WebP / AVIF)
- оптимальний розмір під девайс

```TypeScript
import Image from 'next/image';

<Image src="/hero.png" alt="Hero" width={400} height={300} />
```

5. Оптимізація шрифтів (`next/font`)

- self-hosted шрифти
- відсутність layout shift
- автоматичний preload

```TypeScript
import { Inter } from 'next/font/google';

const inter = Inter({ subsets: ['latin'] });
```

6. Prefetch навігації Next.js

- автоматично prefetch-ить маршрути
- швидка навігація без повного перезавантаження
- працює через `<Link />`

7. Streaming та partial rendering

- HTML віддається частинами
- сторінка починає рендеритись до повного завантаження даних
- покращує TTFB та UX

#### Що важливо розуміти

- Оптимізації вбудовані, а не опціональні
- Next.js заохочує “performance by default”
- Ручна оптимізація потрібна рідко

**Коротко:**

- Next.js автоматично оптимізує рендеринг, JS та assets
- Server Components і code splitting зменшують бандл
- Зображення, шрифти та навігація оптимізуються з коробки

</details>

<details>
<summary>9. Як працюють змінні середовища в Next.js?</summary>

#### Next.js

У **Next.js 16+** змінні середовища використовуються для зберігання
конфігурації, секретів та середовищних налаштувань.  
Ключовий принцип — **чітке розділення серверних і клієнтських змінних**.

1. Файли зі змінними середовища

**Next.js автоматично підхоплює такі файли:**

- `.env.local` — локальне середовище (не комітиться)
- `.env.development`
- `.env.production`
- `.env.test`

```env
DATABASE_URL=postgres://...
NEXT_PUBLIC_API_URL=https://api.example.com
```

2. Серверні змінні середовища (за замовчуванням)

**Змінні без префікса `NEXT_PUBLIC_`:**

- доступні лише на сервері
- не потрапляють у JS-бандл
- безпечні для зберігання секретів

```TypeScript
const dbUrl = process.env.DATABASE_URL;
```

**Можна використовувати в:**

- Server Components
- Route Handlers
- Server Actions
- Middleware

3. Клієнтські змінні середовища

**Змінні з префіксом `NEXT_PUBLIC_`:**

- доступні в браузері
- інжектяться під час білду
- не є секретами

```TypeScript
const apiUrl = process.env.NEXT*PUBLIC_API_URL;
```

Усі `NEXT_PUBLIC_*` значення видимі користувачу.

4. Використання в App Router

**Server Component (безпечний доступ)**

```tsx
export default function Page() {
  return <div>{process.env.SECRET_KEY}</div>;
}
```

**Client Component (тільки `NEXT_PUBLIC_*`)**

```tsx
'use client';

export default function ClientComp() {
  return <div>{process.env.NEXT_PUBLIC_API_URL}</div>;
}
```

5. Важливі особливості

- Змінні читаються **під час білду**
- Зміна `.env` → потрібен **restart сервера**
- Runtime-змінні підтримуються лише на сервері
- Edge Middleware має обмежений доступ

#### Типові помилки

- Використання секретів з `NEXT_PUBLIC_`
- Доступ до server env у Client Component
- Очікування, що env зміниться без рестарту

**Коротко:**

- Змінні без `NEXT_PUBLIC_` — тільки серверні
- `NEXT_PUBLIC_*` — доступні в браузері
- У Next.js 16+ безпека базується на поділі server / client

</details>

<details>
<summary>10. Яка різниця між клієнтським та серверним рендерингом у Next.js?</summary>

#### Next.js

У **Next.js 16+** клієнтський і серверний рендеринг — це **не взаємовиключні
підходи**, а частини **гібридної архітектури**, побудованої навколо **React
Server Components** та **App Router**.

#### Серверний рендеринг (Server Rendering)

#### Як працює

- HTML генерується **на сервері**
- Дані отримуються під час рендерингу
- У браузер надходить готова розмітка
- Клієнтські компоненти гідратуються після завантаження

#### У Next.js 16+

- Server Components — **за замовчуванням**
- Підтримуються SSR / SSG / ISR
- Data fetching виконується на сервері

```tsx
export default async function Page() {
  const data = await fetch('https://api.example.com/data', {
    cache: 'no-store',
  }).then(res => res.json());

  return <div>{data.title}</div>;
}
```

#### Переваги

- кращий SEO
- швидший first paint
- менший JS-бандл
- безпечна робота з БД і секретами

#### Клієнтський рендеринг (Client Rendering)

**Як працює**

- HTML мінімальний або порожній
- Дані завантажуються в браузері
- UI рендериться після виконання JavaScript

**У Next.js 16+**

- Реалізується через Client Components
- Потрібна директива 'use client'

```tsx
'use client';

import { useEffect, useState } from 'react';

export default function ClientComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('/api/data')
      .then(res => res.json())
      .then(setData);
  }, []);

  return <div>{data?.title}</div>;
}
```

#### Коли використовують

- інтерактивні елементи
- робота з browser-only API
- локальний UI-стан

#### Важливе розуміння для Next.js 16+

- Server Rendering — база за замовчуванням
- Client Rendering використовується точково
- Server + Client компоненти комбінуються в одному дереві

**Коротко:**

- У Next.js 16+ серверний рендеринг — стандарт
- Клієнтський рендеринг потрібен лише для інтерактивності
- Оптимальний підхід — мінімум Client Components, максимум Server Components

</details>

<details>
<summary>11. Як працює файловий роутинг у Next.js?</summary>

#### Next.js

У **Next.js** файловий роутинг реалізований через **App Router** і базується на
структурі папки **`app/`**.  
Кожна папка та спеціальний файл визначають маршрут, layout або поведінку
сторінки **без ручної конфігурації**.

#### Базові принципи файлового роутингу

1. `page.tsx` — сторінка маршруту

Файл `page.tsx` створює **публічний маршрут**.

```txt
app/page.tsx        → /
app/blog/page.tsx   → /blog
```

```tsx
export default function Page() {
  return <h1>Blog</h1>;
}
```

2. `layout.tsx` — спільний layout

`layout.tsx` обгортає всі вкладені сторінки:

```txt
app/layout.tsx        → кореневий layout
app/dashboard/layout.tsx → layout для /dashboard/*
```

```tsx
export default function Layout({ children }: { children: React.ReactNode }) {
  return (
    <html>
      <body>{children}</body>
    </html>
  );
}
```

3. Вкладені маршрути (Nested Routes)

Структура папок визначає вкладеність маршрутів:

```txt
app/dashboard/settings/page.tsx → /dashboard/settings
```

4. Динамічні маршрути

Для параметрів використовуються квадратні дужки:

```txt
app/posts/[id]/page.tsx → /posts/123
```

```tsx
export default function Page({ params }: { params: { id: string } }) {
  return <div>Post {params.id}</div>;
}
```

5. Спеціальні файли маршруту

| Файл            | Призначення                 |
| --------------- | --------------------------- |
| `loading.tsx`   | loading state               |
| `error.tsx`     | error boundary              |
| `not-found.tsx` | 404                         |
| `template.tsx`  | reset state між навігаціями |

6. Route Groups

Папки в дужках не впливають на URL, але допомагають структурувати код:

```txt
app/(auth)/login/page.tsx → /login
```

7. Приватні папки

Папки з `_` не створюють маршрут:

```txt
app/_components/
```

#### Важливі особливості

- Маршрути створюються автоматично
- Немає конфігурації роутів
- App Router підтримує streaming та layouts
- Pages Router використовується лише для legacy-проєктів

**Коротко:**

- Файловий роутинг у Next.js 16+ базується на папці `app/`
- `page.tsx` створює маршрут, `layout.tsx` — спільний UI
- Динамічні маршрути та спеціальні файли керують поведінкою сторінки

</details>

<details>
<summary>12. Як створювати динамічні маршрути в Next.js?</summary>

#### Next.js

У **Next.js** динамічні маршрути створюються за допомогою **квадратних дужок
(`[]`)** у структурі папок **`app/`**.  
Це дозволяє будувати сторінки з параметрами URL **без ручної конфігурації
роутів**.

1. Базовий динамічний маршрут

```txt
app/posts/[id]/page.tsx → /posts/123
```

```tsx
export default function Page({ params }: { params: { id: string } }) {
  return <div>Post ID: {params.id}</div>;
}
```

- id — параметр маршруту
- значення доступне через params

2. Кілька параметрів

```txt
app/users/[userId]/posts/[postId]/page.tsx
→ /users/42/posts/7
```

```tsx
export default function Page({
  params,
}: {
  params: { userId: string; postId: string };
}) {
  return (
    <div>
      User: {params.userId}, Post: {params.postId}
    </div>
  );
}
```

3. Catch-all маршрути

Використовуються для змінної кількості сегментів.

```txt
app/docs/[...slug]/page.tsx
→ /docs/a/b/c
```

```tsx
export default function Page({ params }: { params: { slug: string[] } }) {
  return <div>{params.slug.join('/')}</div>;
}
```

4. Optional catch-all маршрути

```txt
app/docs/[[...slug]]/page.tsx
```

**Працює для:**

- `/docs`
- `/docs/a`
- `/docs/a/b`

5. Data fetching у динамічних маршрутах

```tsx
export default async function Page({ params }: { params: { id: string } }) {
  const post = await fetch(`https://api.example.com/posts/${params.id}`, {
    cache: 'no-store',
  }).then(res => res.json());

  return <h1>{post.title}</h1>;
}
```

6. Генерація статичних маршрутів (SSG)

Для SSG використовують generateStaticParams:

```TypeScript
export async function generateStaticParams() {
  return [{ id: '1' }, { id: '2' }];
}
```

#### Best practices

- Використовувати **Server Components** за замовчуванням
- Валідувати параметри
- Не зловживати catch-all маршрутами
- Поєднувати з layouts для спільного UI

**Коротко:**

- Динамічні маршрути створюються через `[param]`
- `params` містить значення URL
- Підтримуються catch-all та optional маршрути
- Працює з SSR, SSG та ISR

</details>

<details>
<summary>13. Як Next.js обробляє параметри URL у динамічних маршрутах?</summary>

#### Next.js

У **Next.js** параметри URL у динамічних маршрутах обробляються автоматично
через **структуру папок** у `app/`.  
Значення параметрів передаються в сторінку або layout через обʼєкт **`params`**.

1. Доступ до параметрів маршруту

**Для маршруту:**

```txt
app/posts/[id]/page.tsx → /posts/123
```

**Next.js передає параметри як проп:**

```tsx
export default function Page({ params }: { params: { id: string } }) {
  return <div>Post ID: {params.id}</div>;
}
```

- `id` завжди типу `string`
- отримується на сервері

2. Параметри в layouts

Параметри доступні не лише в `page.tsx`, а й у вкладених `layout.tsx`:

```tsx
export default function Layout({
  children,
  params,
}: {
  children: React.ReactNode;
  params: { id: string };
}) {
  return (
    <section>
      <h1>Post {params.id}</h1>
      {children}
    </section>
  );
}
```

3. Catch-all параметри

```txt
app/docs/[...slug]/page.tsx → /docs/a/b/c
```

```tsx
export default function Page({ params }: { params: { slug: string[] } }) {
  return <div>{params.slug.join('/')}</div>;
}
```

- `slug` — масив сегментів URL

4. Optional catch-all параметри

```txt
app/docs/[[...slug]]/page.tsx
```

```tsx
params.slug; // string[] | undefined
```

**Працює для:**

- `/docs`
- `/docs/a`
- `/docs/a/b`

5. Параметри та data fetching

Параметри часто використовуються для серверного data fetching:

```tsx
export default async function Page({ params }: { params: { id: string } }) {
  const data = await fetch(`https://api.example.com/posts/${params.id}`, {
    cache: 'no-store',
  }).then(res => res.json());

  return <h1>{data.title}</h1>;
}
```

6. Валідація параметрів

Next.js не валідовує параметри автоматично, тому:

- перевірка типів
- обробка невалідних значень
- виклик `notFound()`

```TypeScript
import { notFound } from 'next/navigation';

if (!isValid(params.id)) {
  notFound();
}
```

#### Важливі особливості

- `params` доступні лише на сервері
- У Client Components параметри отримують через `useParams()`
- Параметри завжди рядки або масиви рядків

**Коротко:**

- URL-параметри передаються через `params`
- Працюють у `page.tsx` і `layout.tsx`
- Підтримуються dynamic, catch-all і optional параметри
- Валідація параметрів — відповідальність розробника

</details>

<details>
<summary>14. Як обробляти маршрути catch-all у Next.js?</summary>

#### Next.js

У **Next.js 16+** catch-all маршрути дозволяють обробляти **змінну кількість
сегментів URL** в одному маршруті.  
Вони реалізуються через **спеціальний синтаксис папок** у директорії `app/`.

1. Catch-all маршрути (`[...param]`)

Catch-all маршрут обробляє **один або більше сегментів** URL.

```txt
app/docs/[...slug]/page.tsx
```

**Відповідає URL:**

- `/docs/a`
- `/docs/a/b`
- `/docs/a/b/c`

```tsx
export default function Page({ params }: { params: { slug: string[] } }) {
  return <div>{params.slug.join('/')}</div>;
}
```

- `slug` — масив рядків
- завжди містить щонайменше один елемент

2. Optional catch-all маршрути (`[[...param]]`)

Optional catch-all дозволяє обробляти нуль або більше сегментів.

```txt
app/docs/[[...slug]]/page.tsx
```

**Відповідає URL:**

- `/docs`
- `/docs/a`
- `/docs/a/b`

```tsx
export default function Page({ params }: { params: { slug?: string[] } }) {
  return <div>{params.slug?.join('/') ?? 'Docs root'}</div>;
}
```

3. Різниця між catch-all і optional catch-all

| Тип           | Сегменти | Значення               |
| ------------- | -------- | ---------------------- |
| `[...slug] `  | 1+       | `string[]`             |
| `[[...slug]]` | 0+       | `string[] / undefined` |

4. Типові кейси використання

**Catch-all маршрути застосовують для:**

- документації
- блогів з вкладеною структурою
- файлових менеджерів
- CMS-сторінок
- breadcrumbs-навігації

5. Data fetching з catch-all

```tsx
export default async function Page({
  params,
}: {
  params: { slug?: string[] };
}) {
  const path = params.slug?.join('/') ?? '';

  const page = await fetch(`https://api.example.com/pages/${path}`, {
    cache: 'no-store',
  }).then(res => res.json());

  return <h1>{page.title}</h1>;
}
```

#### Best practices

- Використовувати catch-all лише за потреби
- Обробляти edge cases (`undefined`)
- Поєднувати з layouts
- Валідувати сегменти URL

**Коротко:**

- Catch-all маршрути обробляють змінну кількість сегментів
- `[...param]` — мінімум один сегмент
- `[[...param]]` — нуль або більше сегментів
- Часто використовуються для docs та CMS

</details>

<details>
<summary>15. Опиши функціональність компонента Link у Next.js.</summary>

#### Next.js

Компонент **`Link`** у **Next.js** використовується для **клієнтської навігації
між маршрутами** без повного перезавантаження сторінки.  
Він є ключовим елементом **App Router** та забезпечує швидку й оптимізовану
навігацію.

#### Основні можливості `Link`

1. Клієнтська навігація (SPA-поведінка)

`Link` виконує перехід між сторінками:

- без перезавантаження браузера
- зі збереженням стану
- з мінімальним JS-навантаженням

```tsx
import Link from 'next/link';

<Link href="/blog">Blog</Link>;
```

2. Автоматичний prefetch

Next.js автоматично prefetch-ить сторінки, на які веде `Link`:

- при появі у viewport
- у фоновому режимі
- тільки для внутрішніх маршрутів

Це значно прискорює навігацію.

3. Інтеграція з App Router

`Link` працює з:

- nested routes
- layouts
- streaming
- loading states

Навігація не скидає layouts і не викликає повний ререндер сторінки.

4. Підтримка динамічних маршрутів

```tsx
<Link href={`/posts/${id}`}>Post</Link>
```

Працює з dynamic та catch-all маршрутами.

5. Accessibility (a11y)

- `Link` рендерить `<a>`
- підтримує клавіатурну навігацію
- коректно працює з screen readers

#### Що не потрібно робити

- використовувати `<a href>` для внутрішньої навігації
- обгортати `Link` в `<a>`
- вручну реалізовувати SPA-навігацію

#### Додаткові можливості

- `prefetch={false}` — вимкнення prefetch
- `replace` — замінює запис у history
- `scroll={false}` — зберігає позицію скролу

```tsx
<Link href="/dashboard" prefetch={false} scroll={false}>
  Dashboard
</Link>
```

**Коротко:**

- `Link` забезпечує швидку клієнтську навігацію
- Автоматично prefetch-ить сторінки
- Глибоко інтегрований з App Router та layouts
- Є стандартом навігації у Next.js

</details>

<details>
<summary>16. Як реалізувати міжсторінкову навігацію (navigation) у Next.js?</summary>

#### Next.js

У **Next.js** міжсторінкова навігація реалізується через **вбудований router App
Router**, який підтримує **декларативну** та **програмну** навігацію без
перезавантаження сторінки.

1. Декларативна навігація через `Link` (основний спосіб)

Компонент `Link` використовується для навігації через UI:

```tsx
import Link from 'next/link';

<Link href="/blog">Blog</Link>;
```

**Коли використовувати:**

- навігаційні меню
- списки
- кнопки-посилання

2. Програмна навігація через `useRouter`

Для навігації у відповідь на події (submit, click, success):

```tsx
'use client';

import { useRouter } from 'next/navigation';

export default function Form() {
  const router = useRouter();

  const onSubmit = async () => {
    await saveData();
    router.push('/dashboard');
  };

  return <button onClick={onSubmit}>Save</button>;
}
```

**Основні методи:**

- `router.push()` — перехід
- `router.replace()` — без history
- `router.back()` — назад
- `router.refresh()` — оновлення даних

3. Навігація після Server Actions

У Server Actions використовується redirect():

```TypeScript
'use server';

import { redirect } from 'next/navigation';

export async function createPost() {
  // логіка
  redirect('/posts');
}
```

4.  Керування URL без навігації

Для читання параметрів URL:

- `useParams()`
- `useSearchParams()`

```tsx
'use client';

import { useSearchParams } from 'next/navigation';

const params = useSearchParams();
```

#### Що не використовують у App Router

- `next/router` (Pages Router)
- ручну роботу з `window.location`

#### Best practices

- `Link` — для UI-навігації
- `useRouter` — для подій
- `redirect` — для серверної логіки
- мінімізувати Client Components

**Коротко:**

- Next.js підтримує декларативну та програмну навігацію
- `Link` — основний інструмент
- `useRouter` та `redirect` — для керування навігацією з логіки

</details>

<details>
<summary>17. Як працює попереднє завантаження сторінок (prefetching) у Next.js?</summary>

#### Next.js

У **Next.js** попереднє завантаження сторінок (**prefetching**) — це
автоматичний механізм, який **завантажує дані та код сторінки заздалегідь**, ще
до переходу користувача.  
Це забезпечує **миттєву навігацію** між сторінками.

#### Як працює prefetching

1. Компонент `<Link />` зʼявляється у viewport
2. Next.js у фоновому режимі:
   - завантажує потрібний JavaScript
   - отримує серверні дані (RSC payload)
3. При кліку сторінка відкривається майже миттєво

Все відбувається **без перезавантаження сторінки**.

#### Prefetching у App Router

- Увімкнений **за замовчуванням**
- Працює тільки для **внутрішніх маршрутів**
- Використовує React Server Components
- Враховує кешування (`fetch`, `revalidate`)

```tsx
import Link from 'next/link';

<Link href="/dashboard">Dashboard</Link>;
```

#### Що саме prefetch-иться

- JS-код сторінки
- RSC-дані
- Layout-и, які ще не були завантажені

**Не prefetch-яться:**

- зовнішні посилання
- сторінки з prefetch={false}

#### Керування prefetching

**Вимкнення prefetch**

```tsx
<Link href="/heavy-page" prefetch={false}>
  Heavy page
</Link>
```

**Коли варто вимикати:**

- важкі сторінки
- рідко використовувані маршрути
- сторінки з персональними даними

#### Вплив на продуктивність

**Плюси:**

- швидша навігація
- кращий UX
- менший TTI

**Мінуси:**

- додаткові фонові запити
- потенційне навантаження на сервер

#### Best practices

- Довіряти default-поведінці
- Не вимикати без причини
- Поєднувати з Server Components та кешуванням

**Коротко:**

- Prefetching автоматично підвантажує сторінки
- Активується через Link
- Значно пришвидшує навігацію
- Може бути вимкнений для окремих маршрутів

</details>

<details>
<summary>18. Як Next.js реалізує code splitting?</summary>

#### Next.js

У **Next.js** **code splitting** реалізований **автоматично** та є частиною
філософії _performance by default_.  
Розробнику **не потрібно вручну налаштовувати поділ коду** — Next.js робить це
на рівні маршрутизації та компонентів.

#### Основні рівні code splitting у Next.js

1. Code splitting за маршрутами

Кожен маршрут (`page.tsx`) отримує **окремий JS-бандл**:

```txt
app/page.tsx        → bundle для /
app/blog/page.tsx   → bundle для /blog
```

Завантажується лише код потрібної сторінки.

2. Code splitting через React Server Components

- Server Components не потрапляють у JS-бандл
- Логіка та data fetching виконуються на сервері
- У браузер передається лише результат

```tsx
export default async function Page() {
  const data = await getData();
  return <div>{data.title}</div>;
}
```

Це суттєво зменшує розмір клієнтського JavaScript.

3. Code splitting для Client Components

Client Components:

- виділяються в окремі чанки
- завантажуються лише за потреби
- ізольовані від серверної логіки

```tsx
'use client';

export function InteractiveButton() {
  return <button>Click</button>;
}
```

4. Динамічний імпорт (next/dynamic)

Для важких або рідко використовуваних компонентів:

```tsx
import dynamic from 'next/dynamic';

const HeavyChart = dynamic(() => import('./HeavyChart'), {
  ssr: false,
});
```

Код завантажиться тільки коли компонент реально потрібен.

#### Як code splitting працює з навігацією

- Next.js prefetch-ить чанки для наступних сторінок
- При кліку чанки вже в кеші
- Навігація виглядає миттєвою

#### Що не потрібно робити

- вручну налаштовувати Webpack
- розбивати код вручну без потреби
- імпортувати великі бібліотеки у Client Components

#### Best practices

- Максимально використовувати Server Components
- Мінімізувати `use client`
- Використовувати dynamic import для важких UI
- Довіряти автоматичному code splitting

**Коротко:**

- Code splitting у Next.js 16+ працює автоматично
- Поділ відбувається за маршрутами та компонентами
- Server Components суттєво зменшують JS-бандл
- Dynamic imports — для важких або опційних частин UI

</details>

<details>
<summary>19. Як Next.js оптимізує початкове завантаження сторінки?</summary>

#### Next.js

У **Next.js 16+** оптимізація початкового завантаження сторінки — це результат
**поєднання кількох автоматичних механізмів**, які зменшують час до першого
рендеру та покращують UX.

#### Ключові механізми оптимізації

1. Server Components за замовчуванням

- більшість компонентів виконуються на сервері
- у браузер потрапляє мінімум JavaScript
- швидший First Contentful Paint (FCP)

```tsx
export default async function Page() {
  const data = await getData();
  return <div>{data.title}</div>;
}
```

2. Автоматичний code splitting

- JS ділиться по маршрутах
- завантажується тільки потрібний код
- зменшення initial bundle

3. Streaming та partial rendering

- HTML віддається частинами
- UI зʼявляється ще до завершення всіх запитів
- користувач бачить контент швидше

4. Prefetching навігації

- наступні сторінки підвантажуються у фоні
- навігація відбувається майже миттєво

5. Оптимізація зображень

`next/image`:

- lazy loading
- адаптивні розміри
- сучасні формати (AVIF / WebP)

6. Оптимізація шрифтів

`next/font`:

- self-hosted
- preload
- без CLS

7. Кешування та revalidation

- контроль кешу через `fetch`
- SSG / ISR зменшують кількість SSR
- швидка доставка контенту

#### Що розробнику робити не потрібно

- вручну оптимізувати бандл
- писати кастомний SSR
- налаштовувати CDN

#### Best practices

- Використовувати Server Components
- Мінімізувати Client Components
- Не вимикати prefetch без потреби
- Правильно керувати кешуванням

**Коротко:**

- Next.js мінімізує JS за рахунок Server Components
- Code splitting і streaming прискорюють рендер
- Зображення та шрифти оптимізуються автоматично
- Більшість оптимізацій працює з коробки

</details>

<details>
<summary>20. Які підходи до data fetching підтримує Next.js?</summary>

#### Next.js

У **Next.js 16+** data fetching є **частиною серверного рендерингу** та тісно
інтегрований з **React Server Components**.  
Основний інструмент — **вбудований `fetch`**, розширений механізмами кешування
та revalidation.

#### Основні підходи до data fetching

1. Server-side data fetching (SSR)

Дані отримуються **на кожен запит**.

```TypeScript
await fetch(url, { cache: 'no-store' });
```

**Коли використовувати:**

- персоналізований контент
- auth-залежні сторінки
- дані, що часто змінюються

2. Static data fetching (SSG)

Дані отримуються під час білду і кешуються.

```TypeScript
await fetch(url);
```

**Коли використовувати:**

- публічні сторінки
- рідко змінюваний контент
- максимальний performance і SEO

3. Incremental Static Regeneration (ISR)

Статичні сторінки з оновленням по таймеру.

```TypeScript
await fetch(url, { next: { revalidate: 60 } });
```

**Коли використовувати:**

- блоги
- каталоги
- контент, що оновлюється періодично

4. Data fetching у Server Components (default)

Server Components:

- виконуються на сервері
- не потрапляють у JS-бандл
- можуть напряму звертатись до БД або API

```tsx
export default async function Page() {
  const data = await getData();
  return <div>{data.title}</div>;
}
```

5. Client-side data fetching

Використовується лише для інтерактивних сценаріїв.

```tsx
'use client';

import { useEffect, useState } from 'react';

export function ClientData() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('/api/data')
      .then(res => res.json())
      .then(setData);
  }, []);

  return <div>{data}</div>;
}
```

**Коли використовувати:**

- real-time UI
- browser-only API
- локальний стан

6. Data fetching через Route Handlers

Для побудови API всередині Next.js:

```TypeScript
// app/api/posts/route.ts
export async function GET() {
  return Response.json({ posts: [] });
}
```

#### Важливі принципи

- `fetch` у Next.js кешується за замовчуванням
- Кеш керується через `cache` та `revalidate`
- `useEffect` не є основним підходом
- Server Components — пріоритет

**Коротко:**

- Next.js підтримує SSR, SSG, ISR і client fetching
- Основний підхід — data fetching у Server Components
- Кешування та revalidation керують поведінкою
- Правильний вибір стратегії критичний для performance

</details>

<details>
<summary>21. Що таке getStaticProps і коли його варто використовувати?</summary>

#### Next.js

**`getStaticProps`** — це функція з **Pages Router**, яка використовувалась для
**Static Site Generation (SSG)**, тобто генерації сторінок **під час білду**.

**У Next.js з App Router `getStaticProps` не використовується.** Він вважається
**legacy API** і застосовується лише для підтримки старих проєктів.

#### Як працював `getStaticProps` (історично)

```TypeScript
export async function getStaticProps() {
  const data = await fetchData();

  return {
    props: { data },
  };
}
```

- виконувався під час білду
- дані передавались у компонент сторінки
- сторінка ставала статичною
- підтримував ISR через revalidate

#### Чому getStaticProps більше не потрібен

**У App Router всі ці задачі вирішуються простіше та гнучкіше:**

Заміна getStaticProps у Next.js

```TypeScript
await fetch(url); // SSG за замовчуванням
```

```TypeScript
await fetch(url, { next: { revalidate: 60 } }); // ISR
```

- data fetching виконується напряму в компоненті
- немає окремих lifecycle-функцій
- працює з Server Components
- менше boilerplate-коду

#### Коли сьогодні можна побачити `getStaticProps`

- у старих проєктах на Pages Router
- під час міграції на App Router
- у legacy-коді

Не використовують у нових проєктах

**Коротко:**

- `getStaticProps` — legacy API Pages Router
- У Next.js 16+ не використовується
- Заміна — `fetch` у Server Components
- Для нових проєктів обирають App Router

</details>

<details>
<summary>22. Що таке getServerSideProps і який тип рендерингу він дозволяє?</summary>

#### Next.js

**`getServerSideProps`** — це функція з **Pages Router**, яка використовувалась
для реалізації **Server-Side Rendering (SSR)**, тобто **рендерингу сторінки на
сервері при кожному запиті**.

**У Next.js з App Router `getServerSideProps` не використовується.** Це **legacy
API**, актуальне лише для підтримки старих проєктів.

#### Як працював `getServerSideProps` (історично)

```TypeScript
export async function getServerSideProps(context) {
  const data = await fetchData(context);

  return {
    props: { data },
  };
}
```

- виконувався на кожен HTTP-запит
- мав доступ до `req`, `res`, cookies, headers
- забезпечував SSR
- сторінка не кешувалась за замовчуванням

#### Який тип рендерингу він дозволяє

**Server-Side Rendering (SSR)**

- HTML генерується при кожному запиті
- підходить для персоналізованого контенту
- актуальні дані на момент запиту

#### Чому `getServerSideProps` більше не потрібен у Next.js 16+

У App Router SSR реалізується без окремих lifecycle-функцій — через керування
кешуванням:

#### Заміна `getServerSideProps` у App Router

```TypeScript
await fetch(url, { cache: 'no-store' });
```

Або примусово:

```TypeScript
export const dynamic = 'force-dynamic';
```

**Переваги нового підходу:**

- data fetching прямо в Server Components
- менше boilerplate-коду
- інтеграція з React Server Components
- краща продуктивність і гнучкість

#### Коли сьогодні можна зустріти `getServerSideProps`

- у legacy-проєктах
- під час міграції з Pages Router
- у старих навчальних матеріалах

**Не використовується в нових проєктах**

**Коротко:**

- `getServerSideProps` дозволяв SSR у Pages Router
- Виконувався на кожен запит
- У Next.js 16+ не використовується
- Заміна — SSR через `fetch` і динамічний рендеринг в App Router

</details>

<details>
<summary>23. Як реалізувати інкрементальну статичну регенерацію (ISR) у Next.js?</summary>

#### Next.js

У **Next.js** **Incremental Static Regeneration (ISR)** дозволяє поєднати
**швидкість статичних сторінок** з **можливістю оновлювати дані без повного
ребілду**.  
ISR реалізується через **керування кешуванням `fetch`** в App Router.

1. Базова реалізація ISR

Щоб увімкнути ISR, потрібно вказати час **revalidation** у `fetch`:

```TypeScript
await fetch('https://api.example.com/posts', {
  next: { revalidate: 60 },
});
```

- сторінка генерується статично
- кеш оновлюється раз на 60 секунд
- користувачі завжди отримують швидкий HTML

2. ISR у Server Components

ISR використовується без окремих функцій, напряму в компоненті:

```TypeScript
export default async function Page() {
  const posts = await fetch(
    'https://api.example.com/posts',
    { next: { revalidate: 300 } }
  ).then(res => res.json());

  return <PostsList posts={posts} />;
}
```

3. ISR для динамічних маршрутів

Для динамічних сторінок ISR поєднується з generateStaticParams:

```TypeScript
export async function generateStaticParams() {
  return [{ id: '1' }, { id: '2' }];
}
await fetch(url, { next: { revalidate: 60 } });
```

4. On-demand revalidation (опціонально)

Next.js підтримує ручне оновлення кешу через Route Handlers:

```TypeScript
import { revalidatePath } from 'next/cache';

revalidatePath('/blog');
```

**Використовується для:**

- CMS
- адмін-панелей
- webhooks

5. Коли використовувати ISR

**ISR доцільний, якщо:**

- контент змінюється нечасто
- важлива швидкість
- небажаний повний rebuild

**Приклади:**

- блоги
- каталоги
- маркетингові сторінки

**Коротко:**

- ISR реалізується через fetch з revalidate
- Працює у Server Components
- Підходить для контенту, що оновлюється періодично
- Не потребує окремих lifecycle-функцій

</details>

<details>
<summary>24. Чи можна виконувати client-side data fetching у Next.js?</summary>

#### Next.js

Так, **у Next.js client-side data fetching можливий**, але він **не є основним
підходом**.  
Next.js побудований навколо **Server Components**, тому клієнтське отримання
даних використовується **лише для специфічних сценаріїв**.

#### Як реалізується client-side data fetching

Client-side data fetching можливий **тільки в Client Components**, які
позначаються директивою `'use client'`.

```tsx
'use client';

import { useEffect, useState } from 'react';

export default function ClientData() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('/api/data')
      .then(res => res.json())
      .then(setData);
  }, []);

  return <div>{data?.title}</div>;
}
```

**Коли client-side data fetching доцільний**

- real-time оновлення (polling, WebSocket)
- робота з browser-only API
- локальний UI-стан
- інтерактивні фільтри / пошук

**Коли не варто використовувати**

- для SEO-критичного контенту
- для початкового рендеру сторінки
- для доступу до секретів
- для основних даних сторінки

#### Best practices

- Мінімізувати `use client`
- Не дублювати server data fetching
- Поєднувати з Server Components
- Використовувати Route Handlers для API

**Коротко:**

- Client-side data fetching підтримується
- Використовується лише у Client Components
- Підходить для інтерактивних сценаріїв
- Основний підхід у Next.js 16+ — server-side data fetching

</details>

<details>
<summary>25. Поясни різницю між useEffect та getStaticProps.</summary>

#### Next.js

`useEffect` і `getStaticProps` — це **принципово різні механізми**, які працюють
**у різних середовищах** і вирішують **різні задачі**.

#### `useEffect`

`useEffect` — це **React-хук**, який виконується **на клієнті після рендеру
компонента**.

```tsx
'use client';

import { useEffect, useState } from 'react';

export default function ClientComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('/api/data')
      .then(res => res.json())
      .then(setData);
  }, []);

  return <div>{data}</div>;
}
```

#### Характеристики:

- виконується в браузері
- працює після першого рендеру
- не впливає на HTML, який отримує пошуковий робот
- підходить для інтерактивних сценаріїв

#### `getStaticProps` (legacy)

`getStaticProps` — це API Pages Router, яке використовувалось для Static Site
Generation (SSG).

```TypeScript
export async function getStaticProps() {
  const data = await fetchData();

  return {
    props: { data },
  };
}
```

#### Характеристики:

- виконувався на сервері під час білду
- генерував статичний HTML
- забезпечував SEO
- не використовується в Next.js 16+ (App Router)

#### Актуальний підхід у Next.js 16+

У App Router обидва кейси замінюються data fetching у Server Components:

```tsx
export default async function Page() {
  const data = await fetch('https://api.example.com/data').then(res =>
    res.json()
  );
  return <div>{data.title}</div>;
}
```

- серверний рендеринг
- SEO
- мінімум JS
- без `useEffect` і `getStaticProps`

**Коротко:**

- `useEffect` — клієнтський хук після рендеру
- `getStaticProps` — server-side SSG (Pages Router)
- У Next.js 16+ обидва замінені data fetching у Server Components

</details>

<details>
<summary>26. Як створити API-роут у Next.js?</summary>

#### Next.js

У **Next.js 16+** API-роути реалізуються через **Route Handlers**, які
розміщуються в директорії **`app/api`**.  
Це сучасна заміна `pages/api/*` і стандартний підхід у **App Router**.

1. Створення API-роуту (Route Handler)

API-роут створюється файлом **`route.ts`** або **`route.js`**.

```txt
app/api/posts/route.ts
```

```TypeScript
// app/api/posts/route.ts
export async function GET() {
  return Response.json({ posts: [] });
}
```

Маршрут буде доступний за адресою:

```txt
GET /api/posts
```

2. Підтримка HTTP-методів

Route Handlers підтримують стандартні HTTP-методи:

- `GET`
- `POST`
- `PUT`
- `PATCH`
- `DELETE`

```TypeScript
export async function POST(request: Request) {
  const body = await request.json();

  return Response.json(
    { success: true, body },
    { status: 201 }
  );
}
```

3. Отримання параметрів та headers

**Query parameters:**

export async function GET(request: Request) { const { searchParams } = new
URL(request.url); const page = searchParams.get('page');

return Response.json({ page }); }

**Headers / cookies:** import { headers, cookies } from 'next/headers';

const token = cookies().get('token'); const userAgent =
headers().get('user-agent');

4. Динамічні API-роути

```txt
app/api/posts/[id]/route.ts
```

```TypeScript
export async function GET(
  _: Request,
  { params }: { params: { id: string } }
) {
  return Response.json({ id: params.id });
}
```

5. Типові кейси використання

- REST API
- backend-for-frontend (BFF)
- проксі до зовнішніх API
- on-demand revalidation
- auth-ендпоінти

#### Best practices

- Використовувати Route Handlers замість Pages API
- Тримати API-логику серверною
- Не повертати секрети
- Поєднувати з Server Actions для мутацій

**Коротко:**

- API-роути в Next.js 16+ створюються через app/api/\*/route.ts
- Підтримуються всі основні HTTP-методи
- Це сучасна заміна pages/api
- Route Handlers — стандарт для бекенд-логіки в App Router

</details>

<details>
<summary>27. Поясни, як обробляти параметри запиту (query parameters) в API-роутах Next.js.</summary>

#### Next.js

У **Next.js 16+** параметри запиту (**query parameters**) в API-роутах
обробляються через **обʼєкт `Request`**, який відповідає стандарту Web Fetch
API.  
Next.js **не використовує власний API** для query — усе базується на `URL` та
`URLSearchParams`.

1. Отримання query parameters

У Route Handler доступний обʼєкт `Request`, з якого можна отримати URL:

```TypeScript
export async function GET(request: Request) {
  const { searchParams } = new URL(request.url);

  const page = searchParams.get('page');
  const limit = searchParams.get('limit');

  return Response.json({ page, limit });
}
```

2. Параметри з дефолтними значеннями

```TypeScript
const page = Number(searchParams.get('page') ?? 1);
const limit = Number(searchParams.get('limit') ?? 10);
```

3. Кілька значень одного параметра

```url
/api/posts?tag=js&tag=next
```

```TypeScript
const tags = searchParams.getAll('tag');
```

4. Обробка та валідація параметрів

Next.js не валідовує query parameters автоматично, тому:

```TypeScript
if (!page || page < 1) {
  return Response.json(
    { error: 'Invalid page' },
    { status: 400 }
  );
}
```

5. Використання з динамічними API-роутами

Query parameters працюють разом із динамічними сегментами:

```url
app/api/posts/[id]/route.ts
```

```TypeScript
export async function GET(
  request: Request,
  { params }: { params: { id: string } }
) {
  const { searchParams } = new URL(request.url);
  const includeComments = searchParams.get('comments');

  return Response.json({
    id: params.id,
    includeComments,
  });
}
```

#### Best practices

- Завжди валідовувати query parameters
- Перетворювати типи (string → number)
- Не довіряти значенням з URL
- Повернути коректні HTTP-статуси

**Коротко:**

- Query parameters обробляються через Request та URLSearchParams
- Підтримуються множинні значення
- Валідація — відповідальність розробника
- Це стандартний Web API підхід у Next.js 16+

</details>

<details>
<summary>28. Як Next.js працює з HTTP-методами в API-роутах?</summary>

#### Next.js

У **Next.js 16+** API-роути реалізуються через **Route Handlers**
(`app/api/**/route.ts`), де **кожен HTTP-метод описується окремою експортованою
функцією**.  
Це відповідає стандартам **Web Fetch API** і робить API-логіку декларативною та
зрозумілою.

1. Підтримувані HTTP-методи

Route Handlers підтримують основні методи:

- `GET` — отримання даних
- `POST` — створення ресурсу
- `PUT` — повне оновлення
- `PATCH` — часткове оновлення
- `DELETE` — видалення

2. Базовий приклад з кількома методами

```TypeScript
// app/api/posts/route.ts
export async function GET() {
  return Response.json({ posts: [] });
}

export async function POST(request: Request) {
  const body = await request.json();
  return Response.json({ created: true, body }, { status: 201 });
}
```

URL:

```bash
/api/posts
```

3. Динамічні API-роути з методами

```txt
app/api/posts/[id]/route.ts
```

```TypeScript
export async function GET(
  \_: Request, { params }: { params: { id: string } }
) {
  return Response.json({ id: params.id });
}

export async function DELETE(
  \_: Request, { params }: { params: { id: string } }
) {
  return Response.json({ deleted: params.id });
}
```

4. Обробка тіла запиту (body)

- `request.json()` — для JSON
- `request.formData()` — для форм
- `request.text()` — для plain text

```TypeScript
export async function PATCH(request: Request) {
  const data = await request.json();
  return Response.json({ updated: data });
}
```

5. HTTP-статуси та заголовки

```TypeScript
return new Response(JSON.stringify({ error: 'Unauthorized' }), {
  status: 401,
  headers: { 'Content-Type': 'application/json' },
});
```

6. Кешування та методи

- `GET` може кешуватись (SSG / ISR)
- `POST`, `PUT`, `PATCH`, `DELETE` — завжди динамічні
- Мутації не кешуються

#### Best practices

- Розділяти логіку по HTTP-методах
- Повертати коректні статуси
- Валідовувати вхідні дані
- Тримати API-роути тонкими (BFF-підхід)
- Для мутацій з UI розглядати Server Actions

**Коротко:**

- HTTP-методи описуються окремими експортами (`GET`, `POST`, тощо)
- Route Handlers відповідають стандарту Fetch API
- `GET` — для читання, інші — для мутацій
- Це сучасний і рекомендований підхід у Next.js 16+

</details>

<details>
<summary>29. Як підключити CSS-модулі у застосунку Next.js?</summary>

#### Next.js

У **Next.js** CSS-модулі — це **вбудований і рекомендований спосіб локальної
стилізації компонентів**.  
Вони забезпечують **scope стилів на рівні компонента**, уникаючи конфліктів
класів.

1. Створення CSS-модуля

CSS-модуль — це файл з суфіксом **`.module.css`**:

```txt
components/
 ├─ Button.tsx
 └─ Button.module.css
```

```CSS
/* Button.module.css */
.button {
  background: black;
  color: white;
  padding: 8px 16px;
}
```

2. Підключення CSS-модуля в компоненті

```tsx
import styles from './Button.module.css';

export function Button() {
  return <button className={styles.button}>Click</button>;
}
```

- `styles.button` — унікальний згенерований клас
- конфлікти імен класів виключені

3. Де можна використовувати CSS-модулі

CSS-модулі можна використовувати:

- у Server Components
- у Client Components
- у будь-яких React-компонентах

Вони не залежать від `'use client'`.

4. CSS-модулі та App Router

У App Router:

- CSS-модулі імпортуються напряму в компоненти
- не потребують глобальної реєстрації
- автоматично оптимізуються та tree-shake-яться

5. Комбінація з іншими стилями

```tsx
import clsx from 'clsx';
import styles from './Card.module.css';

<div className={clsx(styles.card, styles.active)} />;
```

6. Обмеження CSS-модулів

- не можна використовувати для глобальних стилів
- не підходять для reset або typography
- не працюють у `globals.css`

Для глобальних стилів використовується `app/globals.css`.

#### Best practices

- CSS-модулі — для компонентних стилів
- `globals.css` — лише для глобальних правил
- Тримати стилі поруч з компонентом
- Не змішувати CSS-модулі з inline-стилями без потреби

**Коротко:**

- CSS-модулі підключаються через `.module.css`
- Забезпечують локальний scope стилів
- Працюють у Server та Client Components
- Це стандартний спосіб компонентної стилізації в Next.js 16+

</details>

<details>
<summary>30. Чи можна використовувати глобальні стилі в Next.js? Як саме?</summary>

#### Next.js

Так, **у Next.js 16+ глобальні стилі підтримуються**, але їх використання
**строго регламентоване** архітектурою **App Router**.  
Глобальні стилі застосовуються **лише для базових правил**, а не для стилізації
компонентів.

1. Файл глобальних стилів

Глобальні стилі оголошуються у файлі **`globals.css`**.

```txt
app/
 ├─ layout.tsx
 ├─ page.tsx
 └─ globals.css
```

2. Підключення глобальних стилів

Глобальні стилі імпортуються один раз у кореневому layout:

```tsx
// app/layout.tsx
import './globals.css';

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html>
      <body>{children}</body>
    </html>
  );
}
```

Імпорт можливий тільки у layout або entry-файлах, не в компонентах.

3. Що варто писати в глобальних стилях

Глобальні стилі підходять для:

- CSS reset / normalize
- базової typography
- змінних (`:root`)
- тем (dark / light)
- стилів для `body`, `html`

```CSS
/* app/globals.css */
:root {
  --primary: #000;
}

body {
  margin: 0;
  font-family: system-ui;
}
```

4. Що не варто писати в глобальних стилях

- стилі конкретних компонентів
- utility-класи для UI
- логіку, яку можна ізолювати

**Для цього використовують:**

- CSS-модулі
- Tailwind CSS
- CSS-in-JS (обмежено)

5. Глобальні стилі та App Router

- застосовуються до всього застосунку
- автоматично оптимізуються
- працюють у Server та Client Components
- не потребують 'use client'

#### Best practices

- Мінімальний обсяг глобальних стилів
- Компонентні стилі — через CSS-модулі або Tailwind
- Не імпортувати глобальні стилі в компонентах

**Коротко:**

- Глобальні стилі підтримуються в Next.js 16+
- Підключаються через `app/globals.css`
- Імпортуються лише в `layout.tsx`
- Використовуються для базових, а не компонентних стилів

</details>

<details>
<summary>31. Порівняй CSS-in-JS та традиційний CSS у контексті Next.js.</summary>

#### Next.js

У **Next.js** підтримуються **обидва підходи до стилізації** — як **традиційний
CSS**, так і **CSS-in-JS**, але з різним рівнем доцільності та обмеженнями,
особливо в контексті **Server Components**.

#### Традиційний CSS у Next.js

До традиційного CSS у Next.js належать:

- **CSS-модулі (`.module.css`)**
- **глобальні стилі (`globals.css`)**

#### Переваги:

- працює **у Server Components за замовчуванням**
- не потребує `'use client'`
- мінімальний runtime-overhead
- краща продуктивність та менший JS-бандл
- офіційно рекомендований підхід

#### Недоліки:

- менша динамічність стилів
- логіку умовної стилізації потрібно вирішувати через класи

#### CSS-in-JS у Next.js

CSS-in-JS (наприклад, styled-components, emotion):

- стилі описуються безпосередньо в JavaScript
- часто залежать від props та стану

#### Особливості в Next.js 16+:

- потребує **Client Components**
- додає JS у бандл
- складніша інтеграція з Server Components
- може вимагати додаткового налаштування для SSR

#### Переваги:

- висока динамічність стилів
- зручна умовна стилізація
- стилі тісно повʼязані з логікою компонента

#### Недоліки:

- не підходить для Server Components
- збільшує initial JS
- ускладнює архітектуру App Router

#### Рекомендований підхід у Next.js 16+

- **CSS-модулі** — для компонентних стилів
- **globals.css** — для базових стилів
- **CSS-in-JS** — лише за необхідності динамічних стилів
- не використовувати CSS-in-JS без чіткої причини

**Коротко:**

- Традиційний CSS краще інтегрований з App Router
- CSS-in-JS вимагає Client Components і збільшує JS
- У Next.js 16+ рекомендовано мінімізувати CSS-in-JS

</details>

<details>
<summary>32. Як інтегрувати CSS-фреймворки на кшталт Tailwind CSS v4 у Next.js-проєкт?</summary>

#### Next.js

У **Next.js 16+** інтеграція **Tailwind CSS v4** є **максимально простою** та
добре узгоджується з **App Router** і **Server Components**.  
Tailwind v4 позбувся застарілих конфігурацій і працює за принципом _zero-config
by default_.

1. Встановлення Tailwind CSS v4

Найпростіший спосіб — під час створення проєкту:

```bash
npx create-next-app@latest
```

**У CLI обрати:**

Tailwind CSS

**Або додати в існуючий проєкт**

```bash
npm install tailwindcss@latest
```

PostCSS, autoprefixer та додаткові плагіни не потрібні.

2. Глобальні стилі (обовʼязково)

У Tailwind CSS v4 не використовуються директиви

`@tailwind base / components / utilities`.

Єдиний правильний спосіб підключення — через @import.

```CSS
/* app/globals.css */
@import "tailwindcss";
```

3. Підключення глобальних стилів у App Router

```tsx
// app/layout.tsx
import './globals.css';

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  );
}
```

- глобальні стилі імпортуються один раз
- працюють у Server та Client Components
- не потребують `'use client'`

4. Конфігурація Tailwind (опціонально)

У Tailwind v4 `tailwind.config` не є обовʼязковим. Він потрібен лише для
кастомізації (теми, кольори, плагіни).

```TypeScript
// tailwind.config.ts
import type { Config } from 'tailwindcss';

const config: Config = {
  theme: {
    extend: {
      colors: {
        brand: '#000',
      },
    },
  },
};

export default config;
```

Поле content не використовується.

5. Використання Tailwind у компонентах

Tailwind-класи можна використовувати:

- у Server Components
- у Client Components
- без додаткових налаштувань

```tsx
export default function Page() {
  return <h1 className="text-2xl font-bold text-center">Hello Tailwind v4</h1>;
}
```

6. Поєднання з іншими підходами

Tailwind CSS v4 можна комбінувати з:

- CSS-модулями
- clsx / classnames
- умовною стилізацією

```tsx
<div className={clsx('p-4', isActive && 'bg-green-500')} />
```

#### Best practices у Next.js 16+

- Використовувати Tailwind як основний спосіб стилізації
- Мінімізувати глобальні стилі
- Не створювати tailwind.config без потреби
- Поєднувати з Server Components для кращої продуктивності

**Коротко:**

- Tailwind CSS v4 інтегрується через @import "tailwindcss"
- tailwind.config — опціональний, без content
- Повністю сумісний з Next.js 16+ та App Router
- Простий, швидкий і сучасний підхід до стилізації

</details>

<details>
<summary>33. Що таке компонент Image і як він оптимізує продуктивність?</summary>

#### Next.js

Компонент **`Image`** з пакета **`next/image`** — це **вбудований інструмент
оптимізації зображень** у Next.js 16+.  
Він автоматично оптимізує завантаження зображень, зменшуючи **розмір трафіку**,
**час першого рендеру** та **CLS** без ручних налаштувань.

#### Основні оптимізації `Image`

1. Автоматичний lazy loading

- Зображення завантажуються **лише тоді**, коли зʼявляються у viewport
- Зменшує initial load та TTI
- Увімкнений **за замовчуванням**

```tsx
import Image from 'next/image';

<Image src="/hero.png" alt="Hero" width={600} height={400} />;
```

2. Адаптивні розміри (responsive images)

- Next.js генерує кілька версій зображення
- Браузер отримує оптимальний розмір під конкретний екран
- Менше байтів → швидше завантаження

3. Сучасні формати зображень

- Автоматично використовує WebP / AVIF, якщо підтримуються браузером
- Не потребує ручної конвертації

4. Запобігання layout shift (CLS)

- `width` і `height` резервують місце в layout
- Сторінка не «стрибає» під час завантаження

```tsx
<Image src="/photo.jpg" alt="Photo" width={300} height={200} />
```

5. Оптимізація на сервері

- Зображення оптимізуються на сервері або edge
- Кешуються та повторно використовуються
- Працює з локальними та віддаленими зображеннями

6. Пріоритетне завантаження (priority)

Для hero-зображень можна вимкнути lazy loading:

```tsx
<Image src="/hero.png" alt="Hero" width={800} height={500} priority />
```

#### Best practices

- Використовувати `Image` замість `<img>` для контентних зображень
- Завжди вказувати `width` та `height`
- `priority` — лише для above-the-fold
- Для іконок/декору можна використовувати `<img>` або SVG

**Коротко:**

- `Image` — вбудований оптимізатор зображень у Next.js
- Забезпечує lazy loading, responsive sizes та modern formats
- Зменшує CLS і покращує initial load
- Рекомендований для більшості зображень у Next.js 16+

</details>

<details>
<summary>34. Як Next.js працює з шрифтами?</summary>

#### Next.js

У **Next.js** робота зі шрифтами реалізована через вбудований модуль
**`next/font`**, який забезпечує **автоматичну оптимізацію шрифтів** без ручних
`<link>` або сторонніх CDN.  
Це зменшує **CLS**, прискорює **initial load** та покращує **Core Web Vitals**.

#### Основний інструмент — `next/font`

`next/font` дозволяє:

- self-host-ити шрифти
- автоматично preload-ити потрібні файли
- уникати FOIT/FOUT
- мінімізувати CLS

Працює **за замовчуванням** з App Router та Server Components.

1. Google Fonts через `next/font/google`

```TypeScript
// app/fonts.ts
import { Inter } from 'next/font/google';

export const inter = Inter({
  subsets: ['latin'],
  display: 'swap',
});
```

Використання в layout:

```tsx
// app/layout.tsx
import { inter } from './fonts';

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en" className={inter.className}>
      <body>{children}</body>
    </html>
  );
}
```

2. Локальні шрифти через `next/font/local`

```TypeScript
import localFont from 'next/font/local';

export const myFont = localFont({
  src: './MyFont.woff2',
  display: 'swap',
});
```

- шрифти зберігаються у проєкті
- повний контроль над файлами
- ідеально для кастомних брендових шрифтів

3. Оптимізації з коробки

`next/font` автоматично:

- підвантажує лише потрібні glyph-и
- додає `preload`
- генерує fallback
- усуває layout shift

**Не потрібно:**

- `<link rel="preconnect">`
- `<link rel="stylesheet">`
- сторонні CDN для шрифтів

#### Best practices у Next.js

- Використовувати тільки `next/font`
- Підключати шрифти у `layout.tsx`
- Обмежувати кількість font-weights
- Уникати ручних `<link>` до шрифтів

**Коротко:**

- Next.js використовує `next/font` для шрифтів
- Шрифти self-host-яться та preload-яться автоматично
- Значно зменшується CLS і initial load
- Це стандарт і best practice для App Router

</details>

<details>
<summary>35. Як уникнути зайвого JavaScript у клієнтському бандлі?</summary>

#### Next.js

У **Next.js** мінімізація клієнтського JavaScript — ключова перевага
фреймворку.  
Це досягається завдяки **Server Components за замовчуванням**, автоматичному
**code splitting** та чіткому розділенню server/client логіки.

1. Використовувати Server Components за замовчуванням

Усі компоненти в App Router є **Server Components**, якщо явно не вказано
інакше.

```tsx
export default async function Page() {
  const data = await getData();
  return <div>{data.title}</div>;
}
```

- не потрапляють у JS-бандл
- виконуються на сервері
- можуть робити data fetching напряму

2. Мінімізувати використання `'use client'`

Директива `'use client'`:

- переводить компонент у Client Component
- тягне за собою весь dependency tree

```tsx
'use client';
```

**Правило:**

використовувати `use client` лише для інтерактивності.

3. Виносити інтерактивність у дрібні Client Components

**Погано:**

```tsx
'use client';
export default function Page() {
  // велика сторінка стає клієнтською
}
```

**Добре:**

```tsx
export default function Page() {
  return (
    <>
      <StaticContent />
      <ClientButton />
    </>
  );
}
```

```tsx
// ClientButton.tsx
'use client';
export function ClientButton() {
  return <button>Click</button>;
}
```

4. Уникати client-side data fetching без потреби

Не рекомендовано для основного контенту:

```tsx
useEffect(() => {
  fetch('/api/data').then(...);
}, []);
```

Краще:

- data fetching у Server Components
- кешування через `fetch` + `revalidate`

5. Використовувати dynamic import для важких компонентів

```tsx
import dynamic from 'next/dynamic';

const Chart = dynamic(() => import('./Chart'), {
  ssr: false,
});
```

- код завантажується лише за потреби
- зменшує initial bundle

6. Обережно з бібліотеками

- не імпортувати важкі бібліотеки в Client Components
- не використовувати універсальні UI-бібліотеки без аналізу
- віддавати перевагу tree-shakable пакетам

7. Використовувати вбудовані можливості Next.js

- `next/image` замість `<img>`
- `next/font` замість `<link>`
- Server Actions замість client API calls

Це зменшує JS і покращує performance.

**Коротко:**

- Server Components — основний інструмент зменшення JS
- `'use client'` слід використовувати точково
- Інтерактивність виноситься в малі компоненти
- Dynamic imports і server-side data fetching зменшують клієнтський бандл

</details>

<details>
<summary>36. Які переваги деплою Next.js-застосунку на Vercel?</summary>

#### Next.js

**Vercel** — це **офіційна платформа-хостинг для Next.js**, створена тією ж
командою.  
Вона забезпечує **максимальну сумісність з Next.js**, автоматизуючи більшість
продакшен-налаштувань.

#### Ключові переваги деплою на Vercel

1. Zero-config деплой

- не потрібні кастомні сервери
- автоматичний білд та деплой
- повна підтримка App Router

```txt
git push → build → deploy
```

2. Підтримка всіх можливостей Next.js

Vercel з коробки підтримує:

- App Router
- React Server Components
- Server Actions
- Route Handlers
- ISR та on-demand revalidation
- Streaming та partial rendering

Без workaround-ів та кастомних конфігів

3. Edge Network та продуктивність

- глобальна CDN
- edge-функції для Middleware
- мінімальний latency
- кращі Core Web Vitals

4. Автоматичне масштабування

- serverless / edge execution
- масштабування без ручного керування
- стабільна робота при пікових навантаженнях

5. ISR та кешування “як задумано”

- ISR працює нативно
- правильне кешування `fetch`
- revalidation без додаткових налаштувань

На інших хостингах ISR часто обмежений або нестабільний.

6. Preview Deployments

- окремий деплой для кожного PR
- унікальний URL
- зручно для code review та QA

7. Інтеграція з GitHub

- автоматичні деплої з `main` / `develop`
- статуси білду в PR
- швидкий rollback

8. Зручна робота зі змінними середовища

- UI для env variables
- різні env для preview / production
- безпечне зберігання секретів

#### Коли Vercel — найкращий вибір

- сучасні Next.js проєкти
- SEO-критичні застосунки
- стартапи та продакшен MVP
- проєкти з активним ISR та Server Actions

**Коротко:**

- Vercel — офіційна платформа для Next.js
- Повна підтримка App Router і Server Components
- Zero-config деплой і глобальна CDN
- Найкраща сумісність і продуктивність “з коробки”

</details>

<details>
<summary>37. Як налаштувати власні доменні імена при деплої Next.js-застосунку?</summary>

#### Next.js

У **Next.js** налаштування власного домену **не залежить від коду**, а
виконується **на рівні хостинг-платформи**.  
Найпростіший і рекомендований варіант — **деплой на Vercel**, де підтримка
кастомних доменів реалізована _out of the box_.

1. Додавання домену у Vercel

1. Зайти в **Vercel Dashboard**
1. Обрати потрібний проєкт
1. Перейти в **Settings → Domains**
1. Додати домен (наприклад `example.com`)

Vercel автоматично:

- перевірить конфігурацію
- підкаже потрібні DNS-записи

2. Налаштування DNS у доменного провайдера

Залежно від типу домену, Vercel запропонує:

**Варіант A** — apex-домен (`example.com`)

```txt
Type: A
Name: @
Value: 76.76.21.21
```

**Варіант B** — піддомен (www.example.com)

```txt
Type: CNAME
Name: www
Value: cname.vercel-dns.com
```

DNS-записи додаються у панелі керування доменом, не у Next.js.

3. HTTPS і SSL

- Vercel автоматично видає SSL-сертифікат
- HTTPS вмикається без ручних налаштувань
- Сертифікати автоматично оновлюються

Не потрібно налаштовувати Let’s Encrypt вручну.

4. Redirect між www / non-www

Рекомендовано мати єдиний канонічний домен.

**Через Vercel Domains (рекомендовано)**

увімкнути redirect у налаштуваннях домену

**Або через Next.js Middleware**

```TypeScript
import { NextResponse } from 'next/server';
import type { NextRequest } from 'next/server';

export function middleware(req: NextRequest) {
  const url = req.nextUrl;

  if (url.hostname === 'www.example.com') {
    url.hostname = 'example.com';
    return NextResponse.redirect(url);
  }
}
```

5. Кілька доменів / середовищ

Vercel підтримує:

- `example.com` — production
- `preview.example.com` — preview
- auto-generated домени для PR

Це не потребує змін у коді Next.js.

6. Важливі моменти для Next.js 16+

- App Router не потребує додаткової конфігурації
- routing працює однаково для всіх доменів
- ISR, Server Actions і Middleware працюють без змін

#### Best practices

- Використовувати HTTPS завжди
- Налаштувати canonical-домен (www або non-www)
- Не хардкодити домен у коді
- Для env-залежних URL використовувати env variables

**Коротко:**

- Кастомні домени налаштовуються на рівні хостингу
- На Vercel це робиться через Settings → Domains
- SSL і HTTPS вмикаються автоматично
- Next.js не потребує змін у коді для доменів

</details>

<details>
<summary>38. Поясни, як деплоїти Next.js-застосунок з SSR на Netlify.</summary>

#### Next.js

Деплой **Next.js з SSR на Netlify можливий**, але **не є нативним**, як на
Vercel.  
Netlify підтримує Next.js через **Netlify Next.js Runtime**, який транслює
можливості Next.js у **Netlify Functions та Edge Functions**.

1. Базові вимоги

Для SSR на Netlify потрібно:

- Next.js **13+ / 16+**
- App Router
- Node runtime (не static export)
- Пакет **`@netlify/plugin-nextjs`**

`output: 'export'` **НЕ використовується**, бо він вимикає SSR.

2. Підготовка Next.js-проєкту

`next.config.js`

```js
/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: true,
};

module.exports = nextConfig;
```

**Не використовувати:**

```JavaScript
output: 'export'
```

3. Налаштування Netlify

netlify.toml

```toml
[build]
  command = "npm run build"
  publish = ".next"

[[plugins]]
  package = "@netlify/plugin-nextjs"
```

**плагін автоматично:**

- налаштовує SSR
- підключає Netlify Functions
- обробляє routing

4. Як працює SSR на Netlify

- SSR-сторінки → Netlify Serverless Functions
- Middleware → Netlify Edge Functions
- Статичні сторінки → CDN
- ISR → обмежена підтримка

```txt
Request
→ CDN
→ Netlify Function (SSR)
→ HTML
```

5. Data fetching та SSR

SSR працює коректно з:

```TypeScript
await fetch(url, { cache: 'no-store' });
```

**Також автоматично SSR:**

- при використанні cookies / headers
- при `dynamic = 'force-dynamic'`

6. Обмеження Netlify (ВАЖЛИВО)

❗ Порівняно з Vercel

| Можливість      | Vercel     | Netlify            |
| --------------- | ---------- | ------------------ |
| SSR             | ✅ нативно | ⚠️ через functions |
| App Router      | ✅         | ⚠️ частково        |
| Server Actions  | ❌ / ⚠️    | ❌                 |
| ISR             | ✅         | ⚠️ обмежено        |
| Edge Middleware | ✅         | ⚠️                 |

Server Actions у Netlify не підтримуються повноцінно.

7. Коли Netlify — нормальний вибір

- проєкт переважно статичний
- мінімальний SSR
- без Server Actions
- вже існує Netlify-інфраструктура

#### Best practices

- Використовувати SSR лише там, де потрібно
- Основний контент — SSG / ISR
- Уникати Server Actions
- Тестувати SSR-флоу окремо

**Коротко:**

- SSR у Next.js 16+ на Netlify можливий через `@netlify/plugin-nextjs`
- SSR реалізується через Netlify Functions
- Підтримка App Router — часткова
- Є обмеження щодо ISR та Server Actions
- Vercel залишається більш нативним варіантом для Next.js

</details>

<details>
<summary>39. Яка структура папок рекомендується для великих Next.js-застосунків?</summary>

#### Next.js

У **Next.js** рекомендована структура папок базується на **App Router**,
**розділенні відповідальностей** та **feature-oriented підході**.  
Мета — зробити код **масштабованим**, **читабельним** і **зручним для команд з
кількох розробників**.

1. Базова структура для великого проєкту

```txt
app/
 ├─ (public)/              # публічні маршрути
 │   ├─ page.tsx
 │   └─ layout.tsx
 ├─ (auth)/                # route group (не впливає на URL)
 │   ├─ login/
 │   └─ register/
 ├─ dashboard/             # feature / domain
 │   ├─ page.tsx
 │   ├─ layout.tsx
 │   └─ loading.tsx
 ├─ api/                   # Route Handlers
 │   └─ users/
 │       └─ route.ts
 ├─ layout.tsx             # root layout
 └─ globals.css
```

- `app/` — єдине джерело маршрутів
- route groups `(( ))` — для логічного групування
- кожен feature має власний layout і стани

2. Feature-oriented структура (рекомендовано)

Для великих застосунків краще групувати код за фічами, а не за типами файлів.

```txt
features/
 ├─ auth/
 │   ├─ components/
 │   ├─ actions.ts
 │   ├─ services.ts
 │   └─ types.ts
 ├─ dashboard/
 │   ├─ components/
 │   ├─ queries.ts
 │   └─ utils.ts
```

**Це:**

- спрощує навігацію в коді
- зменшує coupling
- полегшує рефакторинг

3. Загальні папки (shared / core)

```txt
components/        # спільні UI-компоненти
lib/               # server-side helpers (db, auth, fetch)
hooks/             # client hooks
styles/            # CSS-модулі / tokens
types/             # глобальні TypeScript типи
```

**Важливо:**

- `lib/` — тільки серверний код
- `hooks/` — тільки client-side
- `components/` — без бізнес-логіки

4. Розділення server / client логіки

Рекомендовано явно відокремлювати:

```txt
lib/
 ├─ db.ts          # server-only
 ├─ auth.ts        # server-only
components/
 ├─ Button.tsx     # server або client
 └─ Modal.client.tsx
```

**Або через директорії:**

```txt
server/
client/
```

5. Що не рекомендується

- одна велика папка components для всього
- змішувати server і client код без структури
- глибока вкладеність без сенсу
- дублювання логіки між фічами

6. Best practices для великих команд

- Використовувати route groups
- Тримати мінімум Client Components
- Feature-based структура
- Єдині правила неймінгу
- Документувати архітектуру в README

**Коротко:**

- Основа — app/ з App Router
- Feature-oriented структура — найкращий вибір
- Route groups допомагають логічно організувати маршрути
- Чітке розділення server / client коду — must-have

</details>

<details>
<summary>40. Як організувати компоненти для кращої масштабованості?</summary>

#### Next.js

У **Next.js** масштабованість компонентів досягається завдяки **Server
Components за замовчуванням**, **feature-oriented підходу** та **чіткому
розділенню відповідальностей**.  
Ключова ідея — **менше Client Components, більше композиції**.

1. Використовувати Server Components як стандарт

У App Router всі компоненти є серверними, якщо явно не вказано `'use client'`.

```tsx
export default async function Page() {
  const data = await getData();
  return <List items={data} />;
}
```

Переваги:

не потрапляють у клієнтський бандл

безпечний доступ до БД/секретів

краща продуктивність

2. Виносити інтерактивність у малі Client Components

Погано (великий клієнтський компонент):

```tsx
'use client';
export default function Page() {
  /* багато логіки */
}
```

Добре (точкова інтерактивність):

```tsx
export default function Page() {
  return (
    <>
      <StaticSection />
      <InteractiveToggle />
    </>
  );
}
```

```tsx
// InteractiveToggle.tsx
'use client';
export function InteractiveToggle() {
  /* мінімум логіки */
}
```

3. Feature-oriented структура (рекомендовано)

Групувати компоненти за фічами, а не за типами.

```txt
features/
 ├─ auth/
 │   ├─ components/
 │   ├─ actions.ts
 │   └─ services.ts
 ├─ dashboard/
 │   ├─ components/
 │   └─ queries.ts
```

Це зменшує coupling і спрощує розвиток.

4. Розділяти “presentational” та “container” компоненти

**Presentational** — UI без бізнес-логіки **Container** — data fetching та
orchestration (частіше серверні)

```tsx
// Container (Server Component)
export default async function UsersSection() {
  const users = await getUsers();
  return <UsersList users={users} />;
}
// Presentational
export function UsersList({ users }) {
  return users.map(u => <div key={u.id}>{u.name}</div>);
}
```

5. Уникати “god components”

- Один компонент робить все
- Композиція з дрібних компонентів

```tsx
<Page>
  <Header />
  <Filters />
  <Table />
  <Pagination />
</Page>
```

6. Чітко розділяти server / client код

**Рекомендації:**

- серверна логіка → `lib/`, `actions.ts`, `services.ts`
- клієнтська логіка → `hooks/`, `.client.tsx`
- не імпортувати server-код у Client Components

7. Стандартизувати неймінг і правила

- `*.client.tsx` — клієнтські компоненти
- `*.server.ts` — серверні утиліти
- Єдині правила імпортів та структури
- Документувати патерни в README

**Коротко:**

- Server Components — база для масштабованості
- Client Components — лише для інтерактивності
- Feature-oriented структура спрощує розвиток
- Композиція > великі монолітні компоненти

</details>
