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
