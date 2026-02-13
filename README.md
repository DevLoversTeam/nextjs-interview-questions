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

<details>
<summary>41. Які best practices з безпеки варто враховувати в Next.js-застосунку?</summary>

#### Next.js

У **Next.js** безпека значною мірою базується на **Server Components**,
**ізоляції клієнтського коду** та **контролі доступу на сервері**.  
Фреймворк дає сильну основу, але відповідальність за коректне використання — на
розробнику.

1. Розділяти server та client код

- Server Components **не потрапляють у клієнтський бандл**
- Секрети та бізнес-логіка мають залишатися **на сервері**

```TypeScript
// ❌ не використовувати в Client Components
process.env.SECRET_KEY;
// ✅ тільки Server Components / Route Handlers
const secret = process.env.SECRET_KEY;
```

2. Правильно використовувати змінні середовища

- не зберігати секрети з `NEXT_PUBLIC_`
- використовувати `NEXT_PUBLIC_` лише для публічних значень
- зберігати секрети тільки на сервері

3. Захищати API-роути та Server Actions

- перевіряти автентифікацію
- перевіряти ролі та права доступу
- не довіряти даним з клієнта

```TypeScript
if (!user || user.role !== 'admin') {
  return new Response('Forbidden', { status: 403 });
}
```

4. Використовувати Middleware для pre-request перевірок

Middleware підходить для:

- auth-gate
- редиректів
- захисту приватних маршрутів

```TypeScript
export function middleware(req: NextRequest) {
  if (!isAuthenticated(req)) {
    return NextResponse.redirect(new URL('/login', req.url));
  }
}
```

5. Захист від XSS

- не використовувати dangerouslySetInnerHTML без санітизації
- довіряти React-escaping за замовчуванням
- санітизувати HTML з CMS

6. Захист від CSRF

- використовувати same-site cookies
- перевіряти origin / headers
- для форм — Server Actions замість client fetch

7. Валідація вхідних даних

- не довіряти params, searchParams, body
- валідовувати всі дані
- повертати коректні HTTP-статуси

```TypeScript
if (!isValid(id)) {
  notFound();
  }
```

8. Обмежувати доступ до cookies та headers

- використовувати httpOnly, secure, sameSite
- не читати cookies у Client Components
- працювати з cookies тільки на сервері

9. Мінімізувати attack surface

- мінімум API-ендпоінтів
- мінімум Client Components
- мінімум зовнішніх бібліотек
- видаляти невикористаний код

10. Покладатися на платформу (Vercel / Netlify)

- HTTPS за замовчуванням
- захист від DDoS
- ізоляція serverless-функцій
- автоматичні security updates

**Коротко:**

- Server Components — основа безпеки в Next.js 16+
- Секрети ніколи не потрапляють у клієнт
- API та Server Actions мають бути захищені
- Валідація, auth і мінімізація Client Components — ключові принципи

</details>

<details>
<summary>42. Як Next.js працює з cookies?</summary>

#### Next.js

У **Next.js 16+** робота з cookies відбувається **виключно на сервері** через
вбудовані API App Router.  
Cookies вважаються **частиною серверного контексту**, тому вони тісно
інтегровані з **Server Components**, **Route Handlers**, **Server Actions** та
**Middleware**.

1. Основний API для роботи з cookies

Next.js надає хелпер **`cookies()`** з модуля `next/headers`.

```TypeScript
import { cookies } from 'next/headers';
```

Це стандартний і рекомендований спосіб роботи з cookies у Next.js 16+.

2. Читання cookies (Server Components)

```tsx
import { cookies } from 'next/headers';

export default function Page() {
  const cookieStore = cookies();
  const theme = cookieStore.get('theme');

  return <div>Theme: {theme?.value}</div>;
}
```

- працює лише на сервері
- автоматично робить сторінку динамічною (SSR)

3. Запис і видалення cookies (Server Actions / Route Handlers)

**Запис cookies**

```TypeScript
'use server';

import { cookies } from 'next/headers';

export async function setTheme() {
  cookies().set('theme', 'dark', {
    httpOnly: true,
    secure: true,
    sameSite: 'lax',
  });
}
```

**Видалення cookies**

```TypeScript
cookies().delete('theme');
```

**У Server Components cookies можна лише читати**, але не змінювати.

4. Cookies в API-роутах (Route Handlers)

```TypeScript
import { cookies } from 'next/headers';

export async function GET() {
  const token = cookies().get('token');

  return Response.json({ token: token?.value });
}
```

5. Cookies у Middleware

Middleware часто використовується для:

- auth-gate
- редиректів
- перевірки сесій

```TypeScript
import { NextResponse } from 'next/server';
import type { NextRequest } from 'next/server';

export function middleware(req: NextRequest) {
  const token = req.cookies.get('token');

  if (!token) {
    return NextResponse.redirect(new URL('/login', req.url));
  }
}
```

6. Cookies і Client Components

**Client Components не мають прямого доступу до cookies.**

- немає `document.cookie`
- немає `cookies()`

Єдиний варіант:

- передати значення з сервера через props
- або отримати дані через API

7. Вплив cookies на рендеринг

Використання cookies:

- автоматично вимикає static rendering
- сторінка стає SSR
- кешування за замовчуванням не застосовується

Це очікувана і коректна поведінка.

#### Best practices

- Працювати з cookies тільки на сервері
- Для auth використовувати `httpOnly` cookies
- Не зберігати чутливі дані у client-accessible cookies
- Не читати cookies в Client Components
- Використовувати Server Actions для мутацій

**Коротко:**

- Cookies у Next.js — серверна відповідальність
- Читання: Server Components, Route Handlers, Middleware
- Запис: Server Actions або API-роути
- Використання cookies робить сторінку динамічною (SSR)

</details>

<details>
<summary>43. Як Next.js працює з headers?</summary>

#### Next.js

У **Next.js** робота з HTTP headers є **серверною відповідальністю** і
інтегрована в **App Router**.  
Headers доступні у **Server Components**, **Route Handlers**, **Server Actions**
та **Middleware**, але **не доступні напряму в Client Components**.

1. Читання headers у Server Components

Для читання headers використовується хелпер **`headers()`** з `next/headers`.

```tsx
import { headers } from 'next/headers';

export default function Page() {
  const headersList = headers();
  const userAgent = headersList.get('user-agent');

  return <div>User-Agent: {userAgent}</div>;
}
```

- працює тільки на сервері
- робить сторінку динамічною (SSR)

2. Headers у Route Handlers (API-роутах)

У Route Handlers headers читаються та встановлюються через стандартний Web Fetch
API.

```TypeScript
export async function GET(request: Request) {
  const auth = request.headers.get('authorization');

  return new Response(JSON.stringify({ auth }), {
    headers: {
      'Content-Type': 'application/json',
      'X-Custom-Header': 'example',
    },
  });
}
```

3. Headers у Server Actions

Server Actions можуть читати headers, але зазвичай не використовуються для їх
зміни напряму — для цього краще підходять Route Handlers або Middleware.

```TypeScript
'use server';

import { headers } from 'next/headers';

export async function action() {
  const locale = headers().get('accept-language');
  return locale;
}
```

4. Headers у Middleware

Middleware виконується до рендерингу і ідеально підходить для роботи з headers:

```TypeScript
import { NextResponse } from 'next/server';
import type { NextRequest } from 'next/server';

export function middleware(req: NextRequest) {
  const res = NextResponse.next();

  res.headers.set('x-app-version', '1.0.0');
  return res;
}
```

Типові кейси:

- auth / access control
- redirects
- A/B testing
- geo-based логіка
- security headers

5. Вплив headers на рендеринг і кеш

Використання headers:

- вимикає static rendering
- сторінка стає **SSR**
- сторінка не кешується за замовчуванням

Це очікувана поведінка, оскільки headers залежать від запиту.

6. Headers і Client Components

**Client Components не мають прямого доступу до headers.**

Допустимі варіанти:

- передати значення з сервера через props
- отримати дані через API

#### Best practices

- Працювати з headers **тільки на сервері**
- Використовувати Middleware для pre-request логіки
- Не читати headers без потреби (впливає на SSR)
- Для безпеки налаштовувати headers централізовано
- Не хардкодити логіку на основі `user-agent` без необхідності

**Коротко:**

- Headers у Next.js доступні лише на сервері
- Читання: Server Components, Route Handlers, Middleware
- Зміна: Route Handlers, Middleware
- Використання headers робить сторінку динамічною (SSR)

</details>

<details>
<summary>44. Як керувати глобальним станом без зовнішніх бібліотек?</summary>

#### Next.js

У **Next.js 16+ (App Router)** глобальний стан часто можна організувати **без
Redux/Zustand** через вбудовані інструменти платформи:

- Server Components
- URL state (`searchParams`)
- cookies
- React Context
- Server Actions

1. Server-first підхід

Більшість "глобальних" даних у Next.js мають серверну природу:

- сесія користувача
- роль/permissions
- дані профілю
- фільтри, що впливають на SSR

Такі дані краще читати в Server Components і передавати вниз через props.

2. URL як джерело істини

Для стану інтерфейсу (пошук, сортування, фільтри, пагінація) використовуй URL:

- стан зберігається у `searchParams`
- легко шарити посилання
- працює з back/forward навігацією

Це часто замінює "глобальний store" для сторінок списків.

3. Cookies для персистентних налаштувань

Для теми, локалі, user preferences:

- читаємо на сервері через `cookies()`
- змінюємо через Server Actions або Route Handlers

Так стан узгоджений між SSR і клієнтом.

4. React Context для client-only глобального стану

Context достатній для невеликого глобального стану в клієнті:

- active tab
- UI-прапорці (sidebar open/close)
- тимчасові interaction-стани

```tsx
'use client';

import { createContext, useContext, useState } from 'react';

const UiContext = createContext<{
  isSidebarOpen: boolean;
  setSidebarOpen: (v: boolean) => void;
} | null>(null);

export function UiProvider({ children }: { children: React.ReactNode }) {
  const [isSidebarOpen, setSidebarOpen] = useState(false);
  return <UiContext.Provider value={{ isSidebarOpen, setSidebarOpen }}>{children}</UiContext.Provider>;
}

export function useUi() {
  const ctx = useContext(UiContext);
  if (!ctx) throw new Error('useUi must be used inside UiProvider');
  return ctx;
}
```

5. Server Actions для мутацій

Замість глобального client-store для синхронізації:

- мутація на сервері через Server Action
- після зміни викликаємо `revalidatePath` / `revalidateTag`

Це дає консистентний стан без дублювання логіки на клієнті.

#### Коли цього вже недостатньо

Подумай про зовнішню state-бібліотеку, якщо:

- великий обсяг client-only стану
- складні залежності між багатьма client-компонентами
- high-frequency updates у браузері (наприклад, редактори/конструктори)

**Коротко:**

- У Next.js глобальний стан часто закривається без бібліотек: server-first + URL + cookies + Context.
- Server Actions замінюють частину client-side синхронізації стану.
- Зовнішній store підключають лише коли реально домінує складний client-only state.

</details>

<details>
<summary>45. Коли доцільно підключати бібліотеки керування станом?</summary>

#### Next.js

У **Next.js** більшість задач керування станом вирішуються через:

- **Server Components**
- **Server Actions**
- **URL / cookies**
- **React Context**

Зовнішні state-бібліотеки потрібні **лише в окремих сценаріях**, коли
стандартних інструментів недостатньо.

#### Коли бібліотеки стану **НЕ потрібні** (типовий випадок)

Не використовуй Redux/Zustand, якщо:

- дані приходять із сервера (SSR / SSG / ISR)
- стан можна зберігати в:
  - URL (фільтри, пошук, пагінація)
  - cookies (auth, preferences)
- мутації виконуються через **Server Actions**
- стан локальний для одного компонента

У більшості Next.js-проєктів цього достатньо.

#### Коли бібліотеки стану **доцільні**

1. Великий клієнтський застосунок (SPA-like)

Якщо багато:

- client-only логіки
- складної взаємодії між компонентами
- стану, що часто змінюється на клієнті

Приклади:

- конструктори (drag & drop)
- дашборди з real-time UI
- складні форми / multi-step flows

2. Глобальний UI-стан, що часто змінюється

Наприклад:

- глобальні модалки
- toast-система
- sidebar / layout state
- client-side кеш

У таких випадках **Zustand або Jotai** — хороший вибір.

3. Real-time дані на клієнті

- WebSocket
- live-оновлення
- streaming UI
- collaborative editing

Server Components тут не підходять.

4. Складна взаємозалежна логіка стану

Коли:

- багато взаємоповʼязаних частин стану
- складні transitions
- потрібна централізована логіка

Тоді може знадобитись **Redux Toolkit**.

#### Коли бібліотеки — **погана ідея**

Для:

- auth
- основних даних сторінки
- даних із БД
- SEO-критичного контенту
- server-side стану

Це повинно жити на сервері.

#### Важливий нюанс для Next.js 16+

State-бібліотеки працюють **лише у Client Components**:

```tsx
'use client';
```

Тому:

- вони збільшують JS-бандл
- погіршують initial load
- не повинні використовуватись без необхідності

**Коротко:**

- У більшості Next.js проєктів state-бібліотеки не потрібні
- Вони виправдані для складного client-side UI або real-time логіки
- Працюють тільки у Client Components
- Підключати їх варто лише при реальній необхідності

</details>

<details>
<summary>46. Яка роль tsconfig.json у Next.js-проєкті?</summary>

#### Next.js

Файл **`tsconfig.json`** визначає, як **TypeScript компілює та перевіряє код** у
Next.js-проєкті.  
У Next.js 16+ цей файл також впливає на:

- типізацію
- alias-імпорти
- перевірку помилок під час build
- роботу редактора (VS Code)

Next.js автоматично створює базову конфігурацію при першому запуску TypeScript.

1. Типова конфігурація Next.js

```json
{
  "compilerOptions": {
    "target": "ESNext",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "strict": true,
    "noEmit": true,
    "module": "esnext",
    "moduleResolution": "bundler",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true,
    "baseUrl": ".",
    "paths": {
      "@/*": ["./*"]
    }
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx"],
  "exclude": ["node_modules"]
}
```

2. Основні ролі `tsconfig.json`

**Type checking**

- перевірка типів під час розробки та build
- `strict: true` — рекомендується для production

Alias-імпорти

```json
{
  "baseUrl": ".",
  "paths": {
    "@/*": ["./*"]
  }
}
```

Використання:

```TypeScript
import Button from '@/components/Button';
```

Переваги:

- короткі імпорти
- менше `../../../`
- зручність у великих проєктах

**Контроль компіляції**

- `noEmit: true` — Next.js сам керує збіркою
- TypeScript використовується тільки для перевірки типів

3. Взаємодія з Next.js

Next.js:

- автоматично читає `tsconfig.json`
- оптимізує збірку через SWC
- показує TypeScript-помилки під час next build
- створює `next-env.d.ts`

Якщо є TypeScript-помилки — build може впасти.

4. Важливі опції для Next.js 16+

| Опція                       | Навіщо                       |
| --------------------------- | ---------------------------- |
| `strict`                    | безпечний код                |
| `moduleResolution: bundler` | коректна робота з App Router |
| `jsx: preserve`             | JSX обробляє Next.js         |
| `incremental`               | швидший type-check           |
| `paths`                     | alias-імпорти                |

5. Що не потрібно робити

- змінювати `module` на `commonjs`
- вимикати `strict` у production
- використовувати `emit` — Next.js керує збіркою сам

**Коротко:**

- `tsconfig.json` керує TypeScript-перевіркою та налаштуваннями компіляції
- Використовується для alias-імпортів і strict-режиму
- Next.js читає його під час build
- Це ключовий файл для стабільності та масштабованості проєкту

</details>

<details>
<summary>47. Як визначати типи для сторінок у Next.js?</summary>

#### Next.js

У **Next.js (App Router)** сторінки є **Server Components за замовчуванням**,
тому їх типізація базується на:

- типах props сторінки
- типах `params` для динамічних маршрутів
- типах `searchParams` для query-параметрів

Next.js не використовує спеціальний тип на кшталт `NextPage` (він був у Pages
Router).

1. Базова типізація сторінки

Сторінка — це звичайна функція з типізованими props.

```tsx
export default function Page() {
  return <div>Hello</div>;
}
```

Спеціальні типи не потрібні.

2. Типізація динамічних параметрів (`params`)

Для маршруту:

```bash
app/posts/[id]/page.tsx
```

```tsx
type PageProps = {
  params: {
    id: string;
  };
};

export default function Page({ params }: PageProps) {
  return <div>Post: {params.id}</div>;
}
```

#### Кілька параметрів

```bash
app/users/[userId]/posts/[postId]/page.tsx
```

```tsx
type PageProps = {
  params: {
    userId: string;
    postId: string;
  };
};
```

3. Типізація `searchParams`

```tsx
type PageProps = {
  searchParams: {
    page?: string;
    sort?: string;
  };
};

export default function Page({ searchParams }: PageProps) {
  const page = Number(searchParams.page ?? 1);
  return <div>Page: {page}</div>;
}
```

4. Комбінована типізація

```tsx
type PageProps = {
  params: { id: string };
  searchParams: { tab?: string };
};

export default function Page({ params, searchParams }: PageProps) {
  return (
    <div>
      {params.id} - {searchParams.tab}
    </div>
  );
}
```

5. Типізація для async Server Pages

Сторінки можуть бути async:

```tsx
type PageProps = {
  params: { id: string };
};

export default async function Page({ params }: PageProps) {
  const data = await getPost(params.id);
  return <div>{data.title}</div>;
}
```

6. Типізація `generateStaticParams`

```TypeScript
export async function generateStaticParams(): Promise<
  { id: string }[]
> {
  return [{ id: '1' }, { id: '2' }];
}
```

7. Чого не використовують у Next.js 16+

- `NextPage`
- `GetServerSideProps`
- `GetStaticProps`
- Pages Router типи

#### Best practices

- Описувати окремий тип `PageProps`
- Завжди типізувати `params` для динамічних маршрутів
- Використовувати optional-поля для `searchParams`
- Не використовувати legacy типи з Pages Router

**Коротко:**

- Сторінки в App Router — звичайні функції
- Типізуються через `params` і `searchParams`
- NextPage та інші Pages Router типи не використовуються
- Типізація виконується вручну через PageProps

</details>

<details>
<summary>48. Як мігрувати Next.js-проєкт на TypeScript?</summary>

#### Next.js

У **Next.js 16+** перехід на TypeScript максимально спрощений — фреймворк
автоматично налаштовує більшість конфігурації.  
Міграція може виконуватись **поступово**, без повного переписування проєкту.

1. Встановлення TypeScript

Встановіть необхідні пакети:

```bash
npm install --save-dev typescript @types/react @types/node
```

2. Створення першого TypeScript-файлу

Створіть або перейменуйте будь-який файл:

```css
page.js → page.tsx
```

Після запуску:

```bash
npm run dev
```

Next.js автоматично:

- створить `tsconfig.json`
- створить `next-env.d.ts`
- налаштує рекомендовані опції

3. Поступова міграція (рекомендовано)

Next.js підтримує змішаний код:

```json
"allowJs": true
```

Стратегія:

1. Почати з нових файлів (`.ts / .tsx`)
2. Поступово перейменовувати старі
3. Типізувати ключові частини:

- компоненти
- API
- утиліти
- data fetching

4. Типізація компонентів

```tsx
type Props = {
  title: string;
};

export function Header({ title }: Props) {
  return <h1>{title}</h1>;
}
```

5. Типізація сторінок (App Router)

```tsx
type PageProps = {
  params: { id: string };
};

export default function Page({ params }: PageProps) {
  return <div>{params.id}</div>;
}
```

6. Перевірка типів

Next.js перевіряє типи під час build:

```bash
npm run build
```

Якщо є помилки TypeScript — збірка завершиться з помилкою.

7. Важливі налаштування `tsconfig.json`

Рекомендовано:

```json
{
  "compilerOptions": {
    "strict": true,
    "noEmit": true,
    "moduleResolution": "bundler",
    "incremental": true
  }
}
```

8. Типова стратегія міграції для великих проєктів

1. Увімкнути TypeScript
1. Залишити `allowJs: true`
1. Мігрувати:

- `lib/`
- `components/`
- `features/`

4. В кінці вимкнути allowJs

#### Що не потрібно робити

- переписувати весь проєкт одразу
- вимикати `strict`
- використовувати `any` без потреби
- створювати власний tsconfig з нуля (Next.js генерує оптимальний)

**Коротко:**

- Встановити TypeScript і створити `.ts` або `.tsx`
- Next.js автоматично створює конфігурацію
- Міграцію можна виконувати поступово
- Рекомендовано використовувати `strict` режим

</details>

<details>
<summary>49. Як TypeScript використовується в API-роутах Next.js?</summary>

#### Next.js

У **Next.js** API-роути реалізуються через **Route Handlers**
(`app/api/**/route.ts`) і працюють на базі **Web Fetch API**.  
TypeScript використовується для типізації:

- тіла запиту
- відповіді
- параметрів маршруту (`params`)
- query-параметрів

1. Базовий API-роут з TypeScript

```TypeScript
// app/api/posts/route.ts
export async function GET(): Promise<Response> {
  return Response.json({ posts: [] });
}
```

Next.js автоматично визначає типи, але явне повернення `Promise<Response>` —
good practice.

2. Типізація тіла запиту (POST)

```TypeScript
type CreatePostBody = {
  title: string;
  content: string;
};

export async function POST(request: Request) {
  const body: CreatePostBody = await request.json();

  return Response.json({
    success: true,
    title: body.title,
  });
}
```

Важливо: request.json() повертає any, тому тип потрібно вказувати вручну.

3. Типізація параметрів маршруту (params)

Для маршруту:

```bash
app/api/posts/[id]/route.ts
```

```TypeScript
type RouteParams = {
  params: {
    id: string;
  };
};

export async function GET(
  request: Request,
  { params }: RouteParams
) {
  return Response.json({ id: params.id });
}
```

4. Типізація query parameters

```TypeScript
export async function GET(request: Request) {
  const { searchParams } = new URL(request.url);
  const page = Number(searchParams.get('page') ?? 1);

  return Response.json({ page });
}
```

Для складних кейсів можна створити тип:

```TypeScript
type Query = {
  page?: string;
  limit?: string;
};
```

5. Типізація відповіді

```TypeScript
type PostResponse = {
  id: string;
  title: string;
};

export async function GET(): Promise<Response> {
  const data: PostResponse = {
    id: '1',
    title: 'Hello',
  };

  return Response.json(data);
}
```

6. Використання утиліт для типів

Рекомендовано виносити типи:

```txt
types/
 └─ api.ts
```

```TypeScript
export type CreateUserBody = {
  email: string;
  password: string;
};
```

7. Що не використовується в Next.js 16+

- `NextApiRequest`
- `NextApiResponse`
- `pages/api`
- Express-подібні типи

App Router використовує стандартні:

- `Request`
- `Response`

#### Best practices

- Завжди типізувати `request.json()`
- Виносити типи у `types/`
- Типізувати `params` для динамічних маршрутів
- Не використовувати legacy типи з Pages Router

**Коротко:**

- API-роути в App Router використовують стандартні `Request` і `Response`
- TypeScript типізує body, params і відповіді
- Legacy типи Pages Router не використовуються
- Типи краще виносити в окремі файли

</details>

<details>
<summary>50. Як забезпечити type safety у Next.js-проєкті?</summary>

#### Next.js

У **Next.js** type safety досягається через поєднання:

- суворої конфігурації TypeScript
- типізації серверної та клієнтської логіки
- єдиних типів для API і даних
- перевірки типів під час build

Мета — **type-safe потік даних від БД → сервер → UI**.

1. Увімкнути strict-режим

У `tsconfig.json`:

```json
{
  "compilerOptions": {
    "strict": true,
    "noImplicitAny": true
  }
}
```

Це основа type safety.

2. Типізувати сторінки та маршрути

```tsx
type PageProps = {
  params: { id: string };
  searchParams: { page?: string };
};

export default function Page({ params }: PageProps) {
  return <div>{params.id}</div>;
}
```

3. Типізувати data fetching

```tsx
type Post = {
  id: string;
  title: string;
};

async function getPost(id: string): Promise<Post> {
  const res = await fetch(`/api/posts/${id}`);
  return res.json();
}
```

Ніколи не залишати `any`.

4. Спільні типи для клієнта і сервера

```txt
types/
 └─ post.ts
```

```TypeScript
export type Post = {
  id: string;
  title: string;
};
```

Використовувати:

- у Route Handlers
- у Server Components
- у Client Components

5. Типізація API-роутів

```TypeScript
type CreatePostBody = {
  title: string;
};

export async function POST(request: Request) {
  const body: CreatePostBody = await request.json();
  return Response.json(body);
}
```

6. Runtime-валидація (важливо)

TypeScript перевіряє на етапі компіляції, але не в runtime. Для повної безпеки
використовують схеми (наприклад, Zod).

```tsx
import { z } from 'zod';

const schema = z.object({
  title: z.string(),
});

const body = schema.parse(await request.json());
```

7. Типізація Server Actions

```TypeScript
'use server';

type FormDataType = {
  email: string;
};

export async function submit(data: FormDataType) {
  // type-safe
}
```

8. Уникати `any`

Якщо потрібно тимчасово:

```TypeScript
unknown // краще ніж any
```

9. Типізувати env-змінні

Створити:

```TypeScript
env.d.ts
declare namespace NodeJS {
  interface ProcessEnv {
    DATABASE_URL: string;
  }
}
```

10. Перевірка під час build

Next.js запускає type-check під час:

```bush
npm run build
```

Якщо є помилки — build падає.

#### Архітектурні принципи type safety

- Server Components як джерело істини
- Спільні типи (`types/`)
- Runtime-валидація для зовнішніх даних
- Мінімум Client Components
- Відсутність `any`

**Коротко:**

- Увімкнути `strict` режим
- Використовувати спільні типи для server/client
- Типізувати API, сторінки та data fetching
- Додати runtime-валидацію для зовнішніх даних
- Не використовувати `any`

</details>

<details>
<summary>51. У чому концептуальна різниця між Pages Router та App Router?</summary>

#### Next.js

**Pages Router** і **App Router** — це два різні підходи до побудови застосунку
в Next.js.  
Головна різниця — в **архітектурній моделі рендерингу, роботи з даними та
розділенні server/client логіки**.

У **Next.js 16+** основним і рекомендованим є **App Router**.

1. Архітектурна модель

| Pages Router                      | App Router                  |
| --------------------------------- | --------------------------- |
| React SPA + SSR/SSG через функції | Server-first архітектура    |
| Більшість логіки на клієнті       | Більшість логіки на сервері |
| Сторінки в `pages/`               | Маршрути в `app/`           |

2. Робота з даними

**Pages Router**

Використовує спеціальні lifecycle-функції:

- `getServerSideProps`
- `getStaticProps`
- `getInitialProps`

```TypeScript
export async function getServerSideProps() {}
```

**App Router**

Data fetching виконується напряму в компоненті:

```tsx
export default async function Page() {
  const data = await fetch(url);
  return <div>{data.title}</div>;
}
```

Переваги:

- менше boilerplate
- вбудоване кешування
- ISR через `revalidate`

3. Server Components (ключова відмінність)

**Pages Router**

- всі компоненти — Client Components

**App Router**

- Server Compon`ents за замовчуванням
- `'use client'` лише за потреби

Це дає:

- менший JS-бандл
- кращу продуктивність
- безпечний доступ до БД/секретів

4. Layout і вкладеність

**Pages Router**

- один `_app.tsx`
- один `_document.tsx`

**App Router**

Підтримує вкладені layout-и:

```txt
app/
 ├─ layout.tsx
 ├─ dashboard/
 │   ├─ layout.tsx
 │   └─ page.tsx
```

Також доступні:

- `loading.tsx`
- `error.tsx`
- `not-found.tsx`

5. Нові можливості App Router

- React Server Components
- Streaming
- Server Actions
- Route Handlers (`app/api`)
- Кешування на рівні `fetch`
- Route Groups

Ці можливості відсутні або обмежені у Pages Router.

6. Порівняння

| Критерій          | Pages Router      | App Router         |
| ----------------- | ----------------- | ------------------ |
| Server Components | ❌                | ✅                 |
| Data fetching     | lifecycle-функції | fetch у компоненті |
| Layout nesting    | ❌                | ✅                 |
| Streaming         | ❌                | ✅                 |
| Server Actions    | ❌                | ✅                 |
| Статус            | Legacy            | Standard           |

1. Коли використовується Pages Router

- legacy-проєкти
- поступова міграція
- старі бібліотеки

Нові проєкти — тільки App Router.

**Коротко:**

- Pages Router — legacy клієнт-орієнтований підхід
- App Router — server-first архітектура
- Data fetching через `fetch` замість lifecycle-функцій
- App Router — стандарт у Next.js 16+

</details>

<details>
<summary>52. Як працює файловий роутинг в App Router?</summary>

#### Next.js

У **Next.js** файловий роутинг базується на структурі папки **`app/`**.  
Кожна папка відповідає **URL-сегменту**, а спеціальні файли визначають, що саме
рендериться для цього маршруту.

1. Базовий принцип

Структура папок = URL.

```txt
app/
 ├─ page.tsx
 ├─ about/
 │   └─ page.tsx
 └─ blog/
     └─ page.tsx
```

Відповідні маршрути:

```bash
/           → app/page.tsx
/about      → app/about/page.tsx
/blog       → app/blog/page.tsx
```

Файл `page.tsx` є точкою входу для маршруту.

2. Layout-и

Файл `layout.tsx` створює спільний інтерфейс для сегмента та його вкладених
маршрутів.

```txt
app/
 ├─ layout.tsx
 ├─ dashboard/
 │   ├─ layout.tsx
 │   └─ page.tsx
```

- Root layout — для всього застосунку
- Вкладені layout-и — для конкретних секцій
- Layout-и зберігаються між переходами

3. Динамічні маршрути

```txt
app/posts/[id]/page.tsx
```

URL:

```bash
/posts/123
```

Доступ до параметра:

```tsx
export default function Page({ params }: { params: { id: string } }) {
  return <div>{params.id}</div>;
}
```

4. Route Groups (логічне групування)

Папки в дужках не впливають на URL:

```txt
app/
 ├─ (auth)/
 │   └─ login/page.tsx
```

URL:

```bash
/login
```

Використовується для:

- розділення layout-ів
- організації коду

5. Спеціальні файли App Router

| Файл            | Призначення         |
| --------------- | ------------------- |
| `page.tsx`      | сторінка            |
| `layout.tsx`    | layout              |
| `loading.tsx`   | стан завантаження   |
| `error.tsx`     | обробка помилок     |
| `not-found.tsx` | 404 для сегмента    |
| `route.ts`      | API (Route Handler) |

6. Catch-all маршрути

```txt
app/docs/[...slug]/page.tsx
```

URL:

```css
/docs/a/b/c
```

```tsx
params.slug; // ['a', 'b', 'c']
```

Optional catch-all:

```txt
[[...slug]]
```

7. Вкладеність маршрутів

App Router підтримує глибоку вкладеність:

```txt
app/
 └─ dashboard/
     └─ settings/
         └─ profile/
             └─ page.tsx
```

URL:

```bash
/dashboard/settings/profile
```

#### Важливі особливості

- Server Components за замовчуванням
- Layout-и зберігають стан між переходами
- Streaming і loading працюють на рівні сегментів
- Роутинг автоматичний — без ручних конфігурацій

**Коротко:**

- Маршрути формуються структурою папки `app/`
- `page.tsx` — сторінка, `layout.tsx` — спільний UI
- Підтримуються динамічні, catch-all і route groups
- App Router забезпечує server-first і сегментну архітектуру

</details>

<details>
<summary>53. Що таке Server Components і навіщо вони потрібні?</summary>

#### Next.js

**Server Components** — це компоненти, які **виконуються на сервері**, а їх
результат (HTML + мінімальні дані) передається в браузер.

У **Next.js 16+ (App Router)** всі компоненти є **Server Components за
замовчуванням**.  
Client Components потрібно явно позначати директивою:

```tsx
'use client';
```

1. Як працюють Server Components

Процес рендерингу:

- Компонент виконується на сервері
- Виконується data fetching (БД, API, файли)
- Формується HTML + спеціальний payload
- У браузер відправляється без JavaScript компонента

```tsx
export default async function Page() {
  const posts = await fetch('https://api.example.com/posts').then(r =>
    r.json()
  );

  return <div>{posts.length}</div>;
}
```

2. Головні переваги

**Менший JS-бандл**

Server Components:

- не потрапляють у клієнтський bundle
- зменшують initial load

**Прямий доступ до серверних ресурсів**

Можна безпечно використовувати:

- базу даних
- секрети (`process.env`)
- файлову систему

```TypeScript
const data = await db.post.findMany();
```

**Краща продуктивність**

- менше hydration
- швидший First Load
- менше клієнтської логіки

3. Обмеження Server Components

Server Components не можуть:

- використовувати React hooks (`useState`, `useEffect`)
- працювати з браузерними API
- обробляти клієнтські події (`onClick`)

Для цього потрібен Client Component:

```TypeScript
'use client';

export function Button() {
   const [count, setCount] = useState(0);
   return <button onClick={() => setCount(count + 1)}>{count}</button>;
   }
```

4. Комбінування Server і

Client Server Component може рендерити Client Component:

```tsx
export default function Page() {
  return <Counter />; // Client Component
}
```

Це дозволяє:

- мінімізувати клієнтський JS
- ізолювати інтерактивність

5. Типові use cases

Server Components:

- сторінки
- layout-и
- data fetching
- SEO-контент
- dashboard дані

Client Components:

- форми
- кнопки
- модалки
- анімації

6. Вплив на архітектуру

Next.js 16+ використовує server-first підхід:

- більшість логіки на сервері
- клієнт — тільки для інтерактивності
- менше глобального client-state

**Коротко:**

- Server Components виконуються на сервері і не потрапляють у JS-бандл
- Вони зменшують розмір клієнтського коду і покращують продуктивність
- За замовчуванням всі компоненти в App Router — серверні
- Client Components використовуються лише для інтерактивності

</details>

<details>
<summary>54. У чому різниця між Server Components та Client Components?</summary>

#### Next.js

У **Next.js (App Router)** компоненти поділяються на два типи:

- **Server Components** — виконуються на сервері (за замовчуванням)
- **Client Components** — виконуються у браузері (позначаються `'use client'`)

Головна різниця — **де виконується код і чи потрапляє він у клієнтський
JavaScript-бандл**.

1. Server Components

**Виконання**

- працюють **тільки на сервері**
- їх JavaScript **не відправляється в браузер**

```tsx
export default async function Page() {
  const data = await fetch(url).then(r => r.json());
  return <div>{data.title}</div>;
}
```

**Можливості**

- доступ до БД
- доступ до `process.env`
- робота з cookies / headers
- data fetching

**Обмеження**

Не можна:

- `useState`, `useEffect`
- обробники подій (`onClick`)
- браузерні API (`window`, `localStorage`)

2. Client Components

Позначаються директивою:

```tsx
'use client';
```

**Виконання**

- працюють у браузері
- додаються до JS-бандлу
- проходять hydration

```tsx
'use client';

import { useState } from 'react';

export function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

**Використовуються для**

- інтерактивності
- форм
- модалок
- анімацій
- browser API

3. Основні відмінності

| Критерій                | Server Component | Client Component |
| ----------------------- | ---------------- | ---------------- |
| Де виконується          | Сервер           | Браузер          |
| Потрапляє в JS-бандл    | ❌               | ✅               |
| useState / useEffect    | ❌               | ✅               |
| Event handlers          | ❌               | ✅               |
| Доступ до БД / секретів | ✅               | ❌               |
| SEO / performance       | Вищий            | Нижчий           |

4. Взаємодія між ними

- Server Component може рендерити Client Component
- Client Component не може імпортувати Server Component

```tsx
export default function Page() {
  return <Counter />; // Client Component
}
```

5. Архітектурний принцип Next.js 16+

**Server-first**

- Максимум Server Components
- Client Components — лише там, де потрібна інтерактивність

**Коротко:**

- Server Components — сервер, без JS у браузері
- Client Components — браузер, для інтерактивності
- App Router працює за принципом server-first
- `'use client'` слід використовувати мінімально

</details>

<details>
<summary>55. Для чого використовується директива "use client"?</summary>

#### Next.js

У **Next.js 16+ (App Router)** всі компоненти є **Server Components за
замовчуванням**. Директива **`'use client'`** використовується, щоб позначити
компонент як **Client Component**, який виконується у браузері та підтримує
інтерактивність.

1. Як використовувати

Директива повинна бути першим рядком у файлі:

```tsx
'use client';

import { useState } from 'react';

export default function Counter() {
  const [count, setCount] = useState(0);

  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

Після додавання:

- компонент виконується у браузері
- включається в клієнтський JavaScript-бандл
- проходить hydration

2. Коли потрібен `'use client'`

Використовуй директиву, якщо компонент:

- використовує React hooks (`useState`, `useEffect`, `useReducer`)
- має обробники подій (`onClick`, `onChange`)
- працює з browser API (`window`, `document`, `localStorage`)
- містить інтерактивну логіку (форми, модалки, dropdown тощо)

3. Коли не потрібен

Не додавай `'use client'`, якщо компонент:

- просто відображає дані
- виконує data fetching
- працює з БД або `process.env`
- використовує `cookies` або `headers`
- є layout або сторінкою без інтерактивності

Server Components продуктивніші, бо не додають JavaScript у браузер.

4. Вплив на бандл

Важливо:

- `'use client'` збільшує розмір клієнтського JS
- всі імпорти такого файлу також потрапляють у бандл
- тому директиву слід використовувати мінімально (server-first підхід)

5. Взаємодія з Server Components

- Server Component може рендерити Client Component
- Client Component не може імпортувати Server Component

**Коротко:**

- `'use client'` робить компонент клієнтським (browser execution)
- потрібен для hooks, подій і browser API
- збільшує JS-бандл, тому використовувати тільки там, де є інтерактивність

</details>

<details>
<summary>56. Які обмеження мають Server Components?</summary>

#### Next.js

У **Next.js 16+** Server Components працюють тільки на сервері, тому мають чіткі
обмеження, пов'язані з відсутністю виконання у браузері.

1. Немає React hooks для клієнтського стану та ефектів

Не можна використовувати:

- `useState`
- `useEffect`
- `useReducer`
- `useRef` (для взаємодії з DOM)

Ці hooks потребують виконання в браузері, тому для них потрібен Client Component
(`'use client'`).

2. Немає обробників подій

У Server Component не можна вішати клієнтські події:

- `onClick`
- `onChange`
- `onSubmit`

Причина: серверний компонент рендерить HTML, але не додає клієнтську
інтерактивну логіку.

3. Немає доступу до browser API

Недоступні:

- `window`
- `document`
- `localStorage`
- `sessionStorage`
- `navigator`

Ці API існують лише у середовищі браузера.

4. Не можна імпортувати Server Component у Client Component

Композиція працює так:

- Server Component може рендерити Client Component
- Client Component не може імпортувати Server Component напряму

Це архітектурне правило межі між серверним і клієнтським деревом.

5. Обмеження по сторонніх бібліотеках

Бібліотеки, що залежать від DOM, `window` або React hooks, не працюють у Server
Components без виділення клієнтського шару.

Практично: інтерактивну частину виносять у невеликий Client Component, а решту
залишають server-first.

**Коротко:**

- Server Components не підтримують hooks стану/ефектів, події та browser API.
- Для інтерактивності використовують Client Components з `'use client'`.
- Оптимальна стратегія в Next.js 16+: server-first, client only where needed.

</details>

<details>
<summary>57. Як працює layout і чим він відрізняється від page?</summary>

#### Next.js

У **App Router** ці файли мають різне призначення:

- `page.tsx` — це **контент конкретного маршруту**
- `layout.tsx` — це **спільна оболонка (каркас)** для сегмента маршруту та його
  дочірніх сторінок

1. Як працює `page.tsx`

- відповідає за UI конкретного URL
- є кінцевою точкою маршруту
- рендериться всередині відповідного `layout`

Приклад:

- `app/dashboard/page.tsx` -> `/dashboard`
- `app/dashboard/settings/page.tsx` -> `/dashboard/settings`

2. Як працює `layout.tsx`

- обгортає всі вкладені `page.tsx` і дочірні сегменти
- приймає `children` і рендерить спільну структуру (header, sidebar, nav)
- зберігається між переходами всередині свого сегмента (не перемонтовується як
  сторінка)

Типовий приклад:

```tsx
export default function DashboardLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <section>
      <aside>Sidebar</aside>
      <main>{children}</main>
    </section>
  );
}
```

3. Ключові відмінності

- `page.tsx`:
  - відповідає за унікальний контент конкретного маршруту
  - без `page.tsx` маршрут не матиме сторінки для рендерингу

- `layout.tsx`:
  - перевикористовується для групи маршрутів у сегменті
  - задає спільний каркас і стабільний UI між навігаціями

4. Архітектурна практика в Next.js 16+

- у `layout` виносять те, що має бути спільним між вкладеними сторінками
- у `page` лишають тільки контент конкретного route
- це зменшує дублювання та спрощує підтримку структури застосунку

**Коротко:**

- `page.tsx` = конкретна сторінка маршруту.
- `layout.tsx` = спільна оболонка для сегмента і його дочірніх маршрутів.
- Layout перевикористовується між переходами, page відповідає за унікальний
  контент URL.

</details>

<details>
<summary>58. Що таке вкладені layouts і як вони використовуються?</summary>

#### Next.js

У **Next.js 16+ (App Router)** вкладені layouts (`nested layouts`) це ієрархія
файлів `layout.tsx` у різних сегментах `app/`, де кожен наступний layout
обгортає дочірній маршрут.

Простими словами:

- кореневий `app/layout.tsx` обгортає весь застосунок
- `app/dashboard/layout.tsx` обгортає тільки `/dashboard/*`
- `app/dashboard/settings/layout.tsx` обгортає тільки `/dashboard/settings/*`

1. Як це працює в дереві маршрутів

При переході на глибокий маршрут Next.js збирає layout-и зверху вниз:

- root layout
- layout сегмента
- вкладений layout
- цільовий `page.tsx`

Тобто UI формується шарами, де кожен рівень додає свою спільну оболонку.

2. Навіщо використовувати вкладені layouts

- щоб перевикористовувати спільний UI для групи сторінок
- щоб не дублювати header/sidebar/nav у кожному `page.tsx`
- щоб розділяти зони застосунку (наприклад, публічна частина і dashboard)

3. Практичний приклад структури

```txt
app/
  layout.tsx
  page.tsx
  dashboard/
    layout.tsx
    page.tsx
    settings/
      layout.tsx
      page.tsx
```

Для маршруту `/dashboard/settings` буде застосовано всі три layout-и:

- `app/layout.tsx`
- `app/dashboard/layout.tsx`
- `app/dashboard/settings/layout.tsx`

4. Поведінка під час навігації

- layout зберігає стан і не перемонтовується при переході в межах свого сегмента
- змінюється переважно нижчий рівень (дочірній layout або page)
- це покращує UX і зменшує зайві перерендери спільної оболонки

5. Best practice для Next.js 16+

- тримати layout-и максимально тонкими та відповідальними за каркас
- бізнес-логіку конкретного маршруту лишати в `page.tsx` або серверних модулях
- використовувати вкладення тільки там, де є реальна спільна структура

**Коротко:**

- Вкладені layouts це ієрархія `layout.tsx`, яка шарово обгортає дочірні маршрути.
- Вони прибирають дублювання спільного UI і дають чітку структуру App Router.
- Для глибокого route застосовуються всі layout-и від кореня до поточного сегмента.

</details>

<details>
<summary>59. Як працюють route groups і для чого вони потрібні?</summary>

#### Next.js

У **Next.js 16+ (App Router)** route groups це папки в дужках, наприклад
`(marketing)` або `(dashboard)`, які **організовують структуру маршрутів**, але
**не додають сегмент в URL**.

1. Базовий принцип

- папка `(group)` впливає на файлову структуру, але не на шлях у браузері
- сторінка `app/(marketing)/about/page.tsx` буде доступна за URL `/about`
- group зручний для розділення зон застосунку без зміни адрес

2. Для чого вони потрібні

- логічно розділяти великі частини проєкту (публічна зона, кабінет, адмінка)
- застосовувати різні `layout.tsx` для різних груп сторінок
- тримати чисту архітектуру App Router без штучних сегментів у URL

3. Типовий приклад

```txt
app/
  (marketing)/
    layout.tsx
    page.tsx
    about/page.tsx
  (dashboard)/
    layout.tsx
    dashboard/page.tsx
```

Результат по URL:

- `app/(marketing)/page.tsx` -> `/`
- `app/(marketing)/about/page.tsx` -> `/about`
- `app/(dashboard)/dashboard/page.tsx` -> `/dashboard`

4. Взаємодія з layout

- кожна route group може мати свій `layout.tsx`
- цей layout застосовується до сторінок тільки всередині своєї групи
- так легко мати різні оболонки (наприклад, landing layout і app layout)

5. Важливі зауваження

- route groups не є механізмом безпеки чи доступів, це лише організація маршрутів
- не варто дублювати однакові URL у різних групах без чіткої причини
- використовуй groups для читабельності і масштабованої структури

**Коротко:**

- Route groups це папки виду `(name)`, які не потрапляють у URL.
- Вони потрібні для архітектури: розділення зон і окремих layout-ів.
- Це інструмент структури App Router, а не механізм авторизації.

</details>

<details>
<summary>60. Як реалізуються паралельні маршрути?</summary>

#### Next.js

У **Next.js 16+ (App Router)** паралельні маршрути реалізуються через
**іменовані слоти** (named slots) з папками `@slotName`. Це дозволяє рендерити
кілька незалежних гілок UI одночасно в межах одного layout.

1. Базова ідея

- звичайний `children` це основний слот
- додаткові слоти задаються папками `@analytics`, `@team`, `@feed` тощо
- layout приймає ці слоти як окремі пропси і рендерить у потрібних зонах

2. Приклад структури

```txt
app/dashboard/
  layout.tsx
  @analytics/page.tsx
  @team/page.tsx
  page.tsx
```

3. Приклад layout зі слотами

```tsx
export default function DashboardLayout({
  children,
  analytics,
  team,
}: {
  children: React.ReactNode;
  analytics: React.ReactNode;
  team: React.ReactNode;
}) {
  return (
    <main>
      <section>{children}</section>
      <aside>{analytics}</aside>
      <aside>{team}</aside>
    </main>
  );
}
```

4. Для чого це використовують

- складні дашборди з незалежними панелями
- одночасний показ різних частин інтерфейсу в одному URL-контексті
- краща модульність: кожен слот має свій маршрут і власний рендеринг

5. Важливі нюанси

- паралельні маршрути це не вкладені URL-сегменти, а механіка композиції UI
- кожен слот можна незалежно завантажувати та обробляти через власні `loading.tsx` / `error.tsx`
- підхід добре працює разом із server-first архітектурою App Router

**Коротко:**

- Паралельні маршрути в Next.js робляться через слоти `@slotName`.
- Layout рендерить кілька слотів одночасно як окремі пропси.
- Це зручно для дашбордів і складних сторінок з незалежними UI-блоками.

</details>

<details>
<summary>61. Як працює data fetching у серверних компонентах?</summary>

#### Next.js

У **Next.js 16+ (App Router)** у Server Components дані отримують прямо під час
рендерингу на сервері через `async/await` (найчастіше через `fetch`), без
`useEffect` і без клієнтського запиту після завантаження сторінки.

1. Базовий підхід

Server Component може бути `async`, і ти читаєш дані напряму:

```tsx
export default async function Page() {
  const res = await fetch('https://api.example.com/posts');
  const posts = await res.json();

  return <PostsList posts={posts} />;
}
```

Це працює на сервері, тому користувач отримує вже зрендерений результат.

2. Кешування і режими fetch

У Next.js `fetch` на сервері має керування кешем:

- `cache: 'force-cache'` -> використовує Data Cache
- `cache: 'no-store'` -> завжди запитує свіжі дані на кожен запит
- `next: { revalidate: 60 }` -> ISR-поведінка (перевалідація раз на 60 секунд)

Приклади:

```ts
await fetch(url, { cache: 'force-cache' });
await fetch(url, { cache: 'no-store' });
await fetch(url, { next: { revalidate: 60 } });
```

3. Що це дає в реальних задачах

- швидший first load (дані вже в HTML/Server Render output)
- кращий SEO для контентних сторінок
- менше клієнтського JS, бо не потрібен клієнтський fetch для базового рендеру

4. Повторні запити і ефективність

Next.js дедуплікує однакові `fetch` під час одного рендер-проходу, тому однакові
виклики не мають зайво дублювати мережеві запити в межах запиту.

5. Оновлення даних

Окрім `revalidate` у `fetch`, для on-demand сценаріїв використовують:

- `revalidatePath()`
- `revalidateTag()`

Це дозволяє скидати кеш після змін у БД або CMS.

6. Практичний підхід для співбесіди

- за замовчуванням: Server Components + server-first data fetching
- `no-store` для завжди динамічних даних
- `revalidate`/теги для контрольованого кешу і балансу між свіжістю та швидкістю

**Коротко:**

- У Server Components дані отримують напряму на сервері через `async/await`.
- Керування свіжістю робиться через `cache`, `revalidate`, `revalidatePath`, `revalidateTag`.
- Це дає кращий SEO, менше клієнтського JS і кращу продуктивність App Router.

</details>

<details>
<summary>62. Як Next.js кешує запити fetch?</summary>

#### Next.js

У **Next.js 16+ (App Router)** серверний `fetch` має вбудоване кешування через
**Data Cache**. За замовчуванням Next.js намагається повторно використати
результат запиту (залежно від конфігурації `cache`, `revalidate`, динаміки
маршруту).

1. Базова логіка кешування

- Next.js кешує результат `fetch` на сервері, щоб не робити зайві запити
- кешований результат може використовуватись між запитами користувачів
- це зменшує latency і навантаження на API

2. Основні режими

- `cache: 'force-cache'` -> явно кешує результат у Data Cache
- `cache: 'no-store'` -> не кешує, завжди бере свіжі дані
- `next: { revalidate: N }` -> кешує і перевалідує через `N` секунд

Приклад:

```ts
await fetch(url, { cache: 'force-cache' });
await fetch(url, { cache: 'no-store' });
await fetch(url, { next: { revalidate: 120 } });
```

3. Дедуплікація запитів

У межах одного рендеру Next.js дедуплікує однакові `fetch`, щоб не виконувати
той самий HTTP-запит кілька разів.

4. Коли кеш скидається або оновлюється

- автоматично після часу `revalidate`
- вручну через `revalidatePath()`
- вручну через `revalidateTag()` (якщо запит тегований)

5. Практика для App Router

- статичні/рідко змінні дані: `force-cache` або `revalidate`
- часто змінні дані (дашборд, live-статуси): `no-store`
- після мутацій через Server Actions часто роблять on-demand revalidation

**Коротко:**

- Next.js кешує серверні `fetch` у Data Cache для швидшого рендеру.
- Кеш контролюється через `cache`, `next.revalidate`, `revalidatePath`, `revalidateTag`.
- Для динамічних даних використовують `no-store`, для решти кеш + перевалідацію.

</details>

<details>
<summary>63. У чому різниця між force-cache та no-store?</summary>

#### Next.js

У **Next.js 16+ (App Router)** `force-cache` і `no-store` це два протилежні
режими кешування для серверного `fetch`.

1. `force-cache`

- Next.js зберігає результат у Data Cache
- наступні запити можуть отримувати кешовану відповідь
- підходить для даних, які оновлюються рідко

Типові кейси:

- маркетингові сторінки
- довідкові дані
- публічний контент без частих змін

2. `no-store`

- результат `fetch` не кешується
- на кожен HTTP-запит виконується новий запит до джерела даних
- підходить для дуже динамічних даних

Типові кейси:

- live-статуси
- персоналізовані дашборди
- адмін-панелі зі свіжими даними

3. Приклад

```ts
await fetch(url, { cache: 'force-cache' });
await fetch(url, { cache: 'no-store' });
```

4. Практичний вибір

- якщо пріоритет швидкість і можна показати не найсвіжіші дані -> `force-cache`
- якщо пріоритет абсолютна актуальність на кожен запит -> `no-store`
- проміжний варіант: `next: { revalidate: N }`

**Коротко:**

- `force-cache` кешує і пришвидшує рендер.
- `no-store` завжди тягне свіжі дані, але дорожчий по latency.
- Вибір залежить від компромісу між швидкістю та актуальністю.

</details>

<details>
<summary>64. Як працює revalidation даних?</summary>

#### Next.js

У **Next.js 16+** revalidation це механізм оновлення кешованих даних після
певного часу або за подією, щоб поєднати швидкість кешу і актуальність контенту.

1. Time-based revalidation

Для `fetch` задають інтервал у секундах:

```ts
await fetch(url, { next: { revalidate: 60 } });
```

Що це означає:

- дані кешуються
- протягом 60 секунд повертається кеш
- після вікна revalidate Next.js оновлює кеш новими даними

2. On-demand revalidation

Кеш можна скинути вручну після мутації даних:

- `revalidatePath('/posts')`
- `revalidateTag('posts')`

Це типово роблять після Server Actions або змін у CMS/БД.

3. Коли використовувати

- `revalidate: N` для контенту, що оновлюється періодично
- `revalidatePath` коли зміни торкаються конкретного маршруту
- `revalidateTag` коли потрібно інвалідовувати групу запитів за тегом

4. Що важливо на співбесіді

- revalidation не дорівнює `no-store`
- це кероване кешування, а не повна відмова від кешу
- дозволяє отримати кращий баланс продуктивності та свіжості даних

**Коротко:**

- Revalidation оновлює Data Cache за часом або вручну.
- Основні інструменти: `next.revalidate`, `revalidatePath`, `revalidateTag`.
- Це головний механізм "швидко + достатньо свіжо" в App Router.

</details>

<details>
<summary>65. Як реалізується streaming rendering?</summary>

#### Next.js

У **Next.js 16+ (App Router)** streaming rendering дозволяє відправляти HTML
частинами: користувач бачить готові частини сторінки раніше, поки повільні
сегменти ще догружаються.

1. Як це працює

- сервер починає рендер одразу
- готові сегменти UI відправляються в браузер по мірі готовності
- повільні ділянки рендеряться пізніше без блокування всього екрану

2. Роль `loading.tsx`

Для сегмента маршруту можна додати `loading.tsx`:

- він показується миттєво як fallback
- коли дані готові, Next.js підміняє fallback на реальний контент

3. Переваги

- менший TTFB/краще сприйняття швидкості
- користувач раніше бачить каркас сторінки
- повільний запит у частині UI не блокує весь route

4. Де це особливо корисно

- дашборди з кількома незалежними віджетами
- сторінки з важкими блоками (аналітика, таблиці, графіки)
- маршрути з різними джерелами даних

5. Практика для App Router

- розбивати сторінку на логічні сегменти
- використовувати `loading.tsx` на рівні потрібного сегмента
- комбінувати зі Server Components і кешуванням для стабільної продуктивності

**Коротко:**

- Streaming віддає HTML по частинах, а не чекає повного рендеру.
- `loading.tsx` показує fallback, поки сегмент догружається.
- Це покращує perceived performance, особливо на складних сторінках.

</details>

<details>
<summary>66. Для чого використовується Suspense у Next.js?</summary>

#### Next.js

У **Next.js 16+ (App Router)** `Suspense` використовується для поступового
рендеру UI: поки частина дерева чекає дані або lazy-компонент, користувач бачить
fallback, а не порожню сторінку.

1. Основна роль

- ізолює повільний фрагмент інтерфейсу
- показує fallback (`loading state`) локально
- не блокує рендер усієї сторінки

2. Де найчастіше застосовується

- навколо повільних Server Components
- для розділення важких блоків дашборду
- у комбінації з streaming rendering

3. Практичний ефект

- кращий perceived performance
- швидший показ ключового контенту
- плавніша поведінка при повільних джерелах даних

**Коротко:**

- `Suspense` дозволяє рендерити UI частинами через fallback.
- Повільні сегменти не блокують весь екран.
- У Next.js це ключовий інструмент для streaming UX.

</details>

<details>
<summary>67. Як Next.js обробляє loading-стани сторінок?</summary>

#### Next.js

У **App Router** loading-стани обробляються через спеціальний файл
`loading.tsx` на рівні сегмента маршруту.

1. Як це працює

- Next.js автоматично показує `loading.tsx`, поки сегмент рендериться
- коли дані/компонент готові, fallback замінюється реальним UI
- працює разом зі streaming, тому сторінка може відкриватися по частинах

2. Рівні застосування

- `app/loading.tsx` -> глобальний loading для кореня
- `app/dashboard/loading.tsx` -> loading тільки для `/dashboard/*`
- вкладені сегменти можуть мати власні loading-екрани

3. Best practice

- робити lightweight skeleton замість спінера на весь екран
- ставити loading на потрібному рівні сегмента, не занадто високо
- зберігати стабільний layout, щоб уникати “стрибків” UI

**Коротко:**

- Loading-стани в App Router задаються через `loading.tsx`.
- Вони спрацьовують автоматично на рівні відповідного сегмента.
- Найкраще працюють як локальні skeleton-и у streaming-потоці.

</details>

<details>
<summary>68. Як працює error.tsx у App Router?</summary>

#### Next.js

`error.tsx` у **Next.js 16+** це локальна error boundary для сегмента маршруту.
Вона перехоплює помилки рендерингу/виконання в межах сегмента і показує fallback
UI замість падіння всього застосунку.

1. Поведінка

- файл `error.tsx` працює для свого сегмента і дочірніх сегментів
- якщо в сегменті стається помилка, рендериться `error.tsx`
- решта незачеплених частин дерева може залишатися робочою

2. Що отримує компонент

Типово компонент приймає:

- `error` (об'єкт помилки)
- `reset()` для повторної спроби рендеру

3. Практика

- показувати зрозуміле повідомлення + кнопку retry (`reset`)
- не виводити технічні stack traces користувачу
- логувати помилки в monitoring (Sentry тощо)

**Коротко:**

- `error.tsx` це сегментна error boundary в App Router.
- Вона ізолює помилки й не дає “впасти” всій сторінці.
- Через `reset()` можна зробити retry без повного перезавантаження.

</details>

<details>
<summary>69. Як реалізується сторінка not-found?</summary>

#### Next.js

У **App Router** сторінка 404 реалізується через файл `not-found.tsx` і виклик
`notFound()` у серверній логіці.

1. Базовий механізм

- створюєш `not-found.tsx` у потрібному сегменті
- у `page.tsx`/Server Component викликаєш `notFound()`, якщо сутність не знайдена
- Next.js рендерить відповідний not-found UI

2. Рівні

- `app/not-found.tsx` -> глобальний 404
- `app/blog/not-found.tsx` -> локальний 404 для `/blog/*`

3. Коли викликати `notFound()`

- запис у БД відсутній
- slug невалідний
- ресурс недоступний для рендеру як сторінка

**Коротко:**

- 404 в App Router = `not-found.tsx` + `notFound()`.
- Можна мати глобальний і сегментні варіанти not-found.
- Це стандартний спосіб обробки "ресурс не знайдено" в Next.js.

</details>

<details>
<summary>70. Як обробляються помилки під час серверного рендерингу?</summary>

#### Next.js

У **Next.js 16+** під час SSR/Server Components помилки обробляються рівнями:
локально через `error.tsx`, глобально через кореневі boundaries та технічний
логінг на сервері.

1. Локальна ізоляція

- помилка в сегменті -> спрацьовує найближчий `error.tsx`
- інші сегменти маршруту можуть продовжити роботу
- це зменшує blast radius помилки

2. Типові джерела помилок

- падіння зовнішнього API
- некоректні дані/схема відповіді
- runtime-помилки в серверній логіці

3. Практичний підхід

- обгортати зовнішні виклики в валідацію/try-catch
- повертати контрольовані fallback-и
- логувати помилки централізовано (Sentry, APM)

4. Для UX

- показувати user-friendly повідомлення
- давати retry, якщо це тимчасова помилка
- не показувати внутрішні деталі сервера

**Коротко:**

- SSR-помилки в App Router ловляться через сегментні `error.tsx`.
- Помилки треба ізолювати, логувати й показувати контрольований fallback.
- Головна мета: стабільний UX навіть при збоях бекенду.

</details>

<details>
<summary>71. Що таке Route Handlers і чим вони відрізняються від API Routes?</summary>

#### Next.js

**Route Handlers** це серверні endpoint-и в `app/**/route.ts`, які працюють у
моделі App Router. Вони є сучасною заміною `pages/api/*` (API Routes).

1. Що таке Route Handlers

- файли `route.ts`/`route.js` у `app`-структурі
- обробляють HTTP-методи: `GET`, `POST`, `PUT`, `PATCH`, `DELETE` тощо
- повертають `Response` / `NextResponse`

2. Головна різниця з API Routes

- API Routes: старий підхід у `pages/api` (Pages Router)
- Route Handlers: новий підхід App Router, краща інтеграція з сучасною
  серверною архітектурою Next.js

3. Чому в Next.js 16+ обирають Route Handlers

- єдина модель разом з App Router
- зручна інтеграція з Server Components, caching, revalidation
- чистіша структура проєкту без міксу старих і нових патернів

**Коротко:**

- Route Handlers = сучасні API endpoint-и в `app/**/route.ts`.
- API Routes (`pages/api`) це legacy-підхід для Pages Router.
- У Next.js 16+ для нових проєктів використовують Route Handlers.

</details>

<details>
<summary>72. Як реалізувати backend-proxy через Route Handlers?</summary>

#### Next.js

Backend-proxy через Route Handler це endpoint у Next.js, який приймає запит від
клієнта і пересилає його у зовнішній/внутрішній backend, додаючи контроль безпеки,
headers, токени і валідацію.

1. Навіщо це робити

- приховати приватні URL і ключі
- централізувати auth/header policy
- зняти CORS-проблеми для клієнта

2. Базовий приклад

```ts
// app/api/proxy/users/route.ts
import { NextResponse } from 'next/server';

export async function GET() {
  const res = await fetch(`${process.env.API_URL}/users`, {
    headers: { Authorization: `Bearer ${process.env.API_TOKEN}` },
    cache: 'no-store',
  });

  if (!res.ok) {
    return NextResponse.json({ message: 'Upstream error' }, { status: res.status });
  }

  const data = await res.json();
  return NextResponse.json(data);
}
```

3. Best practice

- whitelist дозволених маршрутів
- валідація input і нормалізація помилок
- таймаути/retry для нестабільних upstream-сервісів

**Коротко:**

- Route Handler може виступати проксі-шаром між frontend і backend.
- Це дає контроль безпеки, стабільні контракти і простіший клієнт.
- Ключі/секрети лишаються на сервері Next.js.

</details>

<details>
<summary>73. Як Next.js використовується як BFF (Backend for Frontend)?</summary>

#### Next.js

BFF у Next.js це серверний шар, який адаптує дані і бізнес-операції під потреби
конкретного frontend. У Next.js 16+ це зазвичай реалізують через Route Handlers +
Server Actions + Server Components.

1. Що робить BFF-шар

- агрегує дані з кількох сервісів в один frontend-friendly payload
- інкапсулює авторизацію, ролі, permission checks
- приховує складність backend-сервісів від UI

2. Чим це корисно

- тонший клієнтський код
- менше дублювання запитів у різних компонентах
- єдина точка контролю контрактів даних

3. Типова схема

- UI -> Next.js (BFF) -> зовнішні API/мікросервіси
- BFF повертає вже нормалізовану відповідь під потребу конкретного екрана

4. Практика

- виносити інтеграції у server-only модулі
- тримати policy/security у BFF, не в клієнті
- контролювати кеш і revalidation на серверному шарі

**Коротко:**

- BFF у Next.js це серверний адаптер між UI і backend-сервісами.
- Він централізує auth, агрегацію даних і бізнес-правила для frontend.
- У App Router його будують на Route Handlers, Server Actions і Server Components.

</details>

<details>
<summary>74. Як проксувати запити до зовнішніх API через Next.js?</summary>

#### Next.js

Найчастіше проксування роблять через Route Handlers: клієнт звертається до
`/api/*` у Next.js, а Next.js вже викликає зовнішній API.

1. Базовий флоу

- Client -> `/api/external/...` (Next.js)
- Route Handler додає auth headers/secret/token
- Next.js -> External API
- повернення нормалізованої відповіді клієнту

2. Що обов'язково додати

- обробку помилок upstream API
- timeout і fallback-поведінку
- контроль кешу (`force-cache`/`no-store`/`revalidate`) за типом даних

3. Переваги

- секрети не потрапляють у браузер
- стабільний API-контракт для фронтенду
- простіший контроль логування, rate limiting, audit

**Коротко:**

- Проксі до зовнішніх API в Next.js роблять через Route Handlers.
- Клієнт працює тільки з внутрішнім `/api`, без прямих секретних інтеграцій.
- Це безпечніше і зручніше для централізації server-logic.

</details>

<details>
<summary>75. Як централізувати авторизацію на рівні server-logic?</summary>

#### Next.js

У **Next.js 16+** централізація авторизації робиться на серверному рівні:
Middleware + server-only auth utilities + перевірки у Route Handlers/Server
Actions/Server Components.

1. Базова стратегія

- Middleware: первинний gate (наприклад, редірект на login)
- server auth helper: єдина функція читання сесії/токена/ролей
- серверні entry points (Route Handlers, Actions, RSC): обов'язковий
  permission-check перед бізнес-логікою

2. Що це дає

- однакові правила доступу в усьому застосунку
- мінімум дублювання перевірок по файлах
- відсутність довіри до клієнта для security-рішень

3. Практичні правила

- не перевіряти доступ лише на клієнті
- тримати RBAC/ABAC перевірки в server-only модулях
- повертати стандартизовані `401/403` і логувати security-події

4. Типова архітектура

- `middleware.ts` -> coarse-grained доступ
- `lib/auth/server.ts` -> `getSession()`, `requireRole()`
- виклик `requireRole()` у кожному чутливому server endpoint

**Коротко:**

- Авторизацію централізують у server-logic, не в клієнтських компонентах.
- Middleware + спільні auth-утиліти + перевірки в Route Handlers/Actions.
- Це дає передбачувану безпеку і керований доступ у всьому App Router.

</details>

<details>
<summary>76. Як працює edge-logic у Next.js?</summary>

#### Next.js

Edge-logic у **Next.js 16+** це виконання коду ближче до користувача в Edge Runtime (не в повноцінному Node.js-середовищі).

1. Де використовується

- `middleware.ts`
- Route Handlers з edge runtime
- окремі серверні сценарії, де критична мінімальна затримка

2. Що дає

- меншу latency для глобальної аудиторії
- швидші redirect/rewrite/auth checks
- ранню обробку запиту до потрапляння в основний рендер

3. Обмеження

- не всі Node API доступні
- треба орієнтуватись на Web APIs та edge-сумісні бібліотеки

**Коротко:**

- Edge-logic виконує серверний код географічно ближче до юзера.
- Найчастіше використовується в middleware і edge Route Handlers.
- Дає швидкість, але з обмеженнями runtime.

</details>

<details>
<summary>77. У яких випадках доцільно виконувати логіку на edge-рівні?</summary>

#### Next.js

Edge-рівень доцільний там, де важлива миттєва реакція на запит до рендеру сторінки.

1. Типові кейси

- auth/session gate у middleware
- гео/locale redirects
- A/B routing та feature flags
- bot/filter/security checks

2. Коли не варто

- важкі обчислення
- код, що залежить від Node-only пакетів
- складна бізнес-логіка з довгими I/O операціями

3. Правило вибору

- edge для lightweight pre-processing
- основна бізнес-логіка лишається в server runtime

**Коротко:**

- Edge доречний для швидких перевірок і маршрутизаційних рішень.
- Не підходить для heavy backend-обробки.
- Хороший pattern: edge gate + server core logic.

</details>

<details>
<summary>78. Як реалізувати захищені серверні маршрути?</summary>

#### Next.js

У Next.js 16+ захист серверних маршрутів будують через централізовану auth-перевірку в Route Handlers/Server Actions і (за потреби) middleware як перший бар'єр.

1. Базовий підхід

- витягнути сесію/токен на сервері
- перевірити роль/permission
- повернути `401` або `403`, якщо доступу немає

2. Де перевіряти

- в `app/api/**/route.ts`
- у Server Actions перед змінами даних
- у Server Components для приватного контенту

3. Best practice

- єдиний `requireAuth()` / `requireRole()` helper
- жодної довіри до клієнтських перевірок
- audit/log security подій

**Коротко:**

- Захист роблять на сервері, не на клієнті.
- Route Handlers/Actions мають явний auth + permission check.
- Middleware можна використати як додатковий pre-check.

</details>

<details>
<summary>79. Як працюють Server Actions і яку проблему вони вирішують?</summary>

#### Next.js

Server Actions це серверні функції, які викликаються напряму з UI (найчастіше з форм), без окремого ручного API-ендпойнта.

1. Яку проблему вирішують

- прибирають зайвий boilerplate `form -> client fetch -> API route`
- зменшують розрив між UI і серверною мутацією
- спрощують обробку форм і side-effects

2. Як працюють

- action визначається на сервері
- клієнт/форма викликає її напряму
- код виконується тільки на сервері (з доступом до БД/секретів)

3. Де корисні

- CRUD-операції
- submit форм
- дії, що одразу потребують revalidation

**Коротко:**

- Server Actions це серверні мутації без окремих API-роутів.
- Вони спрощують потік запису даних у App Router.
- Основний плюс: менше коду і краща зв'язка UI + server logic.

</details>

<details>
<summary>80. Як Server Actions можуть замінити API-запити?</summary>

#### Next.js

Server Actions замінюють API-запити в сценаріях, де клієнту не потрібен універсальний HTTP-контракт, а потрібна пряма серверна дія.

1. Було (класично)

- client submit
- `fetch('/api/...')`
- API route
- бізнес-логіка

2. Стало (Server Actions)

- form/button викликає action
- action одразу робить мутацію на сервері
- за потреби викликає `revalidatePath`/`revalidateTag`

3. Коли підходить

- внутрішні форми продукту
- типові create/update/delete дії
- коли важлива простота і контроль server-only логіки

4. Коли API лишається доречним

- публічний API для зовнішніх клієнтів
- інтеграції з іншими системами

**Коротко:**

- Server Actions знімають потребу в багатьох внутрішніх API-запитах.
- Для зовнішнього програмного доступу API-роути все ще потрібні.
- Це про спрощення внутрішніх мутацій у Next.js.

</details>

<details>
<summary>81. Як реалізувати обробку форм без API-роутів?</summary>

#### Next.js

Форма без API-роутів у Next.js 16+ реалізується через Server Action, прив'язану до `action` форми.

1. Базова схема

- форма відправляє `FormData`
- Server Action валідовує і зберігає дані
- виконується revalidation/redirect за потреби

2. Переваги

- менше boilerplate
- серверна валідація в одному місці
- безпечний доступ до БД і секретів

3. Практика

- валідація на сервері обов'язкова
- повертати контрольовані стани помилок
- після успіху оновлювати кеш (`revalidatePath`)

**Коротко:**

- Форми без API-роутів робляться через Server Actions.
- Дані обробляються одразу на сервері через `FormData`.
- Це коротший і безпечніший шлях для CRUD-форм.

</details>

<details>
<summary>82. Як Next.js працює з cookies у Server Actions?</summary>

#### Next.js

У Server Actions cookies читаються і записуються на сервері через API cookies, без доступу до `document.cookie`.

1. Що можна робити

- читати значення cookie для сесії/налаштувань
- встановлювати нові cookie (auth/session/flags)
- видаляти cookie при logout

2. Чому це важливо

- cookie-операції відбуваються в trusted server контексті
- можна безпечно керувати httpOnly/session даними

3. Практичні правила

- чутливі cookie ставити як `httpOnly`, `secure`, `sameSite`
- не тримати секрети в клієнтських cookie без захисту

**Коротко:**

- У Server Actions cookies керуються серверно.
- Це безпечніше за клієнтський доступ до cookie.
- Для auth-cookie важливі `httpOnly` і `secure` параметри.

</details>

<details>
<summary>83. Як обмежити доступ до серверної логіки?</summary>

#### Next.js

Доступ до серверної логіки обмежують комбінацією auth, permission checks і server-only модульної архітектури.

1. Обов'язкові рівні

- authentication (хто користувач)
- authorization (що йому дозволено)
- resource-level checks (чи має доступ до конкретної сутності)

2. Технічна реалізація

- `requireAuth()`/`requireRole()` у кожному чутливому вході
- перевірки в Route Handlers, Server Actions, Server Components
- middleware як ранній gate

3. Додатково

- rate limiting
- audit logging
- стандартизовані `401/403`

**Коротко:**

- Обмеження доступу = auth + permission + перевірка ресурсу.
- Перевірки мають бути у всіх серверних entry points.
- Клієнтські перевірки лише UX, не безпека.

</details>

<details>
<summary>84. Як Next.js запобігає витоку серверного коду в клієнт?</summary>

#### Next.js

Next.js розділяє серверні й клієнтські межі: Server Components не потрапляють у браузерний bundle, а client-code треба явно позначати через `'use client'`.

1. Механізм

- за замовчуванням App Router-компоненти серверні
- серверні модулі не бандляться в клієнт
- межа контролюється графом імпортів

2. Важливі правила

- не імпортувати server-only модулі в Client Components
- secrets тримати лише в серверному коді
- не використовувати `NEXT_PUBLIC_` для секретних значень

3. Практика

- окремі `server` модулі для БД/auth/integrations
- мінімальний `'use client'` footprint

**Коротко:**

- Server Components не відправляються в клієнтський JS.
- Ризик витоку з'являється при неправильних імпортах і env-практиках.
- Рішення: чітка server/client межа і discipline в структурі коду.

</details>

<details>
<summary>85. Як уникнути hydration mismatch?</summary>

#### Next.js

Hydration mismatch виникає, коли HTML з сервера не збігається з першим рендером у браузері.

1. Типові причини

- `Math.random()`, `Date.now()` у рендері
- різний рендер залежно від `window` на першому проході
- неузгоджені локалі/таймзони

2. Як уникати

- детермінований рендер на server і client
- browser-only логіку переносити в `useEffect`
- не змішувати server/client стан без синхронізації

3. Практика

- для часових/рандомних значень рендерити стабільний placeholder
- акуратно використовувати умови на клієнтські API

**Коротко:**

- Mismatch = різний initial UI між сервером і клієнтом.
- Тримай перший рендер детермінованим.
- Browser-only обчислення запускай після hydration.

</details>

<details>
<summary>86. Що таке hydration і як вона працює?</summary>

#### Next.js

Hydration це процес, коли React у браузері “під'єднує” інтерактивність до вже згенерованого сервером HTML.

1. Послідовність

- сервер повертає HTML
- браузер показує контент
- React завантажує JS і прив'язує обробники подій

2. Що важливо

- HTML на сервері має збігатися з першим client render
- інакше з'являються hydration warnings/mismatch

3. Роль у Next.js

- Server Components мінімізують client JS
- hydration потрібна там, де є Client Components

**Коротко:**

- Hydration робить серверний HTML інтерактивним.
- Потрібна узгодженість server/client рендеру.
- Чим менше client-частини, тим легша hydration-навантаженість.

</details>

<details>
<summary>87. Як динамічно підвантажувати компоненти?</summary>

#### Next.js

Динамічне завантаження роблять через `next/dynamic`, щоб не включати важкі компоненти в initial bundle.

1. Базовий приклад

```tsx
import dynamic from 'next/dynamic';

const HeavyChart = dynamic(() => import('./HeavyChart'), {
  loading: () => <p>Loading chart...</p>,
});
```

2. Коли використовувати

- важкі віджети (charts/editors/maps)
- компоненти нижче першого екрану
- рідко використані UI-блоки

3. Ефект

- менший стартовий JS
- швидший first render
- краща контрольована деградація через loading fallback

**Коротко:**

- `next/dynamic` відкладено завантажує компонент.
- Це оптимізує bundle і старт сторінки.
- Особливо корисно для heavy клієнтських модулів.

</details>

<details>
<summary>88. Як аналізувати продуктивність Next.js-застосунку?</summary>

#### Next.js

Продуктивність аналізують у 3 шарах: Web Vitals, bundle size, server/render latency.

1. Ключові метрики

- LCP, CLS, INP
- TTFB для серверних маршрутів
- час до інтерактивності критичних екранів

2. Що перевіряти технічно

- розмір клієнтських chunk'ів
- надмірний `'use client'`
- кеш-політики `fetch` і revalidation

3. Інструменти

- Lighthouse / PageSpeed
- Vercel Analytics / Web Vitals
- APM/Sentry для runtime-помилок і latency

4. Стратегія

- server-first архітектура
- локалізація важких клієнтських компонентів
- контроль cache/revalidate по кожному route

**Коротко:**

- Дивись не лише фронт, а й серверну latency та кеш.
- Найчастіші проблеми: завеликий client bundle і неправильний fetch-cache.
- Регулярний моніторинг важливіший за разову оптимізацію.

</details>

<details>
<summary>89. Як працює metadata API?</summary>

#### Next.js

Metadata API у App Router дозволяє оголошувати SEO/meta-дані декларативно на рівні layout/page.

1. Варіанти

- статично через `export const metadata`
- динамічно через `generateMetadata`

2. Що можна задавати

- `title`, `description`
- Open Graph
- Twitter cards
- canonical та інші meta

3. Переваги

- централізований SEO-підхід
- краща типобезпека і підтримка
- зручне наслідування metadata через layout tree

**Коротко:**

- Metadata API це стандартний SEO-механізм App Router.
- Підтримує static і dynamic metadata.
- Працює на рівні маршруту та layout-ієрархії.

</details>

<details>
<summary>90. Як динамічно керувати SEO-метаданими?</summary>

#### Next.js

Для динамічного SEO використовують `generateMetadata`, де мета формується на основі params або серверних даних.

1. Як працює

- отримуєш `params`/`searchParams`
- за потреби фетчиш дані сутності
- повертаєш об'єкт metadata

2. Типові сценарії

- сторінка товару/статті з унікальним title/description
- локалізовані метадані
- умовні OG-зображення

3. Практика

- fallback metadata на випадок помилок
- не генерувати надто дорогі запити без кеш-стратегії

**Коротко:**

- Dynamic SEO у Next.js робиться через `generateMetadata`.
- Metadata формується з route params і серверних даних.
- Важливо мати fallback і контроль fetch-кешу.

</details>

<details>
<summary>91. Як реалізувати Open Graph metadata?</summary>

#### Next.js

Open Graph задають через Metadata API у полі `openGraph` (статично або в `generateMetadata`).

1. Що зазвичай вказують

- `title`
- `description`
- `url`
- `siteName`
- `images`
- `type`

2. Практика

- унікальні OG-дані для важливих сторінок
- валідні absolute URL для image
- узгодженість OG title/description з основним SEO

3. Чому це важливо

- коректний preview у соцмережах/месенджерах
- кращий CTR при шерінгу

**Коротко:**

- OG metadata в Next.js налаштовується через `openGraph`.
- Найкритичніше: коректні title/description та image URL.
- Це напряму впливає на якість link preview.

</details>

<details>
<summary>92. Як Next.js підтримує i18n?</summary>

#### Next.js

У Next.js i18n зазвичай будують через locale-based routing + словники перекладів на сервері/клієнті.

1. Компоненти підходу

- маршрути з locale-сегментом
- middleware для визначення локалі
- словники/ресурси перекладів

2. Що отримуємо

- різні URL для мов
- локалізований контент і metadata
- контроль fallback-мови

3. Практика

- централізований locale resolver
- однакова структура ключів перекладу
- не змішувати бізнес-дані та i18n-рядки

**Коротко:**

- i18n в Next.js базується на маршрутизації та locale-aware рендері.
- Ключові частини: routing, middleware, translation dictionaries.
- Важливо синхронізувати i18n і SEO metadata.

</details>

<details>
<summary>93. Як працює locale-based routing?</summary>

#### Next.js

Locale-based routing це коли мова є частиною URL і визначає, яку локалізовану версію маршруту рендерити.

1. Принцип

- `/en/...`, `/uk/...` тощо
- locale витягується з сегмента маршруту
- той самий route рендерить інший контент за поточною локаллю

2. Звідки береться locale

- із URL
- з middleware (Accept-Language, cookie, user preference)

3. Практичні плюси

- прозорі SEO-friendly адреси
- явна локалізація на рівні навігації
- просте кешування по locale-сегменту

**Коротко:**

- Locale-based routing робить мову частиною шляху.
- Локаль визначає контент, metadata і навігацію.
- Це стандартна основа багатомовних Next.js-застосунків.

</details>

<details>
<summary>94. Як масштабувати Next.js-застосунок у великій команді?</summary>

#### Next.js

Масштабування у великій команді це про чіткі архітектурні межі, стандарти server/client коду і прогнозовані процеси релізу.

1. Технічна структура

- feature/domain-модулі
- shared UI/infra бібліотеки
- server-only шари для інтеграцій і auth

2. Інженерні практики

- обов'язкові code owners + PR checks
- lint/type/test gates у CI
- контрактні правила для API/даних

3. Продуктивність і стабільність

- server-first підхід
- контроль `'use client'`
- route-level performance budgets

**Коротко:**

- Масштабування = архітектурні межі + процесна дисципліна.
- Треба стандартизувати модульність, тести й релізні gate'и.
- Без цього великий Next.js-кодbase швидко деградує.

</details>

<details>
<summary>95. Як організувати domain-driven структуру проєкту?</summary>

#### Next.js

Domain-driven структура групує код навколо бізнес-доменів, а не технічних шарів типу “components/hooks/utils” в одному місці.

1. Приклад підходу

- `src/domains/billing/...`
- `src/domains/orders/...`
- `src/domains/auth/...`

2. Що всередині домену

- UI для домену
- server actions/handlers
- схеми валідації
- domain services/use-cases

3. Переваги

- менша зв'язаність між модулями
- простіше ownership у команді
- швидше вносити зміни в межах домену

**Коротко:**

- DDD-структура групує код за бізнес-напрямками.
- Кожен домен містить свій UI + server logic + validation.
- Це підвищує масштабованість і командну автономність.

</details>

<details>
<summary>96. Як тестувати Next.js-застосунок?</summary>

#### Next.js

Тестування будують пірамідою: unit -> integration -> e2e, покриваючи окремо UI, server logic і маршрути.

1. Рівні

- unit: утиліти, валідація, domain logic
- integration: компоненти + серверні залежності
- e2e: критичні user flows

2. Що покривати пріоритетно

- auth/permissions
- форми і мутації
- критичні маршрути та SEO-сторінки

3. Практика

- стабільні тести без крихких snapshot-overuse
- mocks тільки там, де справді потрібно
- окремі smoke e2e на deploy

**Коротко:**

- Next.js тестують на кількох рівнях, не лише UI-unit.
- Найвищий пріоритет: auth, data mutations, критичні флоу.
- Регресії краще ловляться комбінацією integration + e2e.

</details>

<details>
<summary>97. Як тестувати серверну логіку та Route Handlers?</summary>

#### Next.js

Серверну логіку і Route Handlers тестують із фокусом на контракти: статуси, валідацію, помилки, авторизацію.

1. Що перевіряти

- коректні `200/201/400/401/403/500`
- перевірки ролей/доступів
- поведінку при збоях upstream API/БД

2. Підхід

- unit для чистих server functions
- integration для handler + залежності
- мінімальні e2e для критичних endpoint-флоу

3. Best practice

- ізолювати бізнес-логіку від transport-шару
- тестувати нормалізацію помилок
- перевіряти edge cases валідації input

**Коротко:**

- Route Handlers тестують як HTTP-контракт + security-поведінку.
- Бізнес-логіку краще виносити окремо й тестувати unit/integration.
- Критично перевіряти error-path, не лише happy-path.

</details>

<details>
<summary>98. Як працюють preview deployments?</summary>

#### Next.js

Preview deployments це тимчасові оточення для кожного PR/гілки, де команда бачить реальну версію змін до merge у production.

1. Навіщо

- швидкий review функціоналу і UI
- перевірка інтеграцій до релізу
- раннє виявлення регресій

2. Типовий процес

- відкрив PR -> автоматично створився preview URL
- QA/PM/design перевірили сценарії
- після approve merge в main

3. Практика

- окремі preview env variables
- smoke tests проти preview URL
- чітка політика доступу до preview

**Коротко:**

- Preview deployment дає ізольоване середовище на кожен PR.
- Це покращує якість review і знижує ризик релізу.
- Добре працює в парі з автоматичними smoke checks.

</details>

<details>
<summary>99. Як Next.js інтегрується з CI/CD?</summary>

#### Next.js

Next.js інтегрується в CI/CD як стандартний web-build pipeline: install -> lint -> typecheck -> test -> build -> deploy.

1. Типовий pipeline

- перевірки якості (ESLint, TypeScript)
- юніт/інтеграційні тести
- `next build`
- деплой у preview/prod середовища

2. Що важливо додати

- blocking checks для PR
- security scanning залежностей
- release gates для production

3. Для стабільності

- однакові Node/toolchain версії
- cache залежностей у CI
- rollback стратегія

**Коротко:**

- CI/CD для Next.js це автоматизований quality gate + build + deploy.
- Ключове: незмінні перевірки перед merge та прод-релізом.
- Pipeline має бути відтворюваним і передбачуваним.

</details>

<details>
<summary>100. Які архітектурні рішення роблять Next.js-застосунок стабільним у довгостроковій перспективі?</summary>

#### Next.js

Довгострокова стабільність у Next.js досягається поєднанням server-first архітектури, чітких модульних меж і жорсткої інженерної дисципліни.

1. Архітектурний фундамент

- App Router + Server Components за замовчуванням
- мінімальний `'use client'`
- централізований server layer для auth/integrations

2. Керування даними

- явна cache/revalidation стратегія на рівні маршрутів
- контрольовані мутації через Server Actions/Route Handlers
- стандартизована обробка помилок

3. Командна масштабованість

- domain-driven структура
- code ownership і технічні стандарти
- обов'язкові тести та CI gates

4. Операційна надійність

- спостережуваність (logs/metrics/tracing)
- preview deployments + поступові релізи
- чіткий rollback і incident-процес

**Коротко:**

- Стабільність дає не один патерн, а системна архітектура + процеси.
- Server-first, чіткі модулі, стандартизовані дані й помилки.
- Без дисципліни CI/тестів/моніторингу довгострокова якість не тримається.

</details>
