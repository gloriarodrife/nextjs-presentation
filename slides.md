---
theme: default
css: ./styles.css
---

# Next.js

<div class="w-16 h-1 bg-emerald-600 my-4"></div>

_A modern web development framework for high-performance applications_

---
class: flex flex-col
---

## What is a Framework vs Vanilla JavaScript?

<div class="grid grid-cols-2 gap-6 my-auto">

  <div class="p-5 rounded-xl bg-white shadow border border-emerald-900/10">
    <h3 class="text-emerald-800 font-bold text-lg mb-2">🌱 Vanilla JavaScript</h3>
    <p class="text-sm text-gray-700 leading-relaxed">
      Building an app with plain JavaScript means you have to write everything from scratch. You manually handle DOM elements, routing, and setup without any pre-made structure. This forces the browser to download and process heavy JavaScript bundles before showing anything.
    </p>
  </div>

  <div class="p-5 rounded-xl bg-white shadow border border-emerald-900/10">
    <h3 class="text-emerald-800 font-bold text-lg mb-2">🏗️ Framework (Like Next.js)</h3>
    <p class="text-sm text-gray-700 leading-relaxed">
      A framework is a <strong>pre-made structure</strong> for your project. It gives you basic rules, built-in tools, and automated routing so you can focus only on building your features instead of wasting time on manual configurations.
    </p>
  </div>

</div>

---
zoom: 0.8
class: flex flex-col
---

## Vanilla JS: creating an "About" page

<div class="my-auto">

**1. `index.html`**: the base page

```html
<div id="app"></div>
<script src="script.js"></script>
```

**2. `script.js`**: manual routing + DOM

```javascript
const app = document.getElementById('app');
if (window.location.pathname === '/about') {
  app.innerHTML = '<h1>About Us</h1>';
}
```

**3. Server config**: so `/about` loads `index.html` instead of a 404

```javascript
import express from 'express';
const app = express();

// Serve static files (index.html, script.js)
app.use(express.static('public'));

// Any other route (/about, /contact...) returns index.html
app.use((req, res) => {
  res.sendFile('index.html', { root: 'public' });
});

app.listen(3000);
```

</div>

---
class: flex flex-col
---

## Next.js: creating an "About" page

<div class="my-auto">

```bash
npx create-next-app@latest my-app
cd my-app
npm run dev
```

Open `http://localhost:3000` and you already have a working server.


```tsx
// app/about/page.js
export default function About() {
  return <h1>About Us</h1>;
}
```

Next.js automatically gives you:

- ✅ The HTML structure
- ✅ The `/about` route
- ✅ The server

</div>

---
class: flex flex-col
---

## The difference ⚖️

<div class="my-auto">

<div class="rounded-2xl overflow-hidden shadow-lg border border-emerald-900/10 bg-white">
  <table class="w-full text-sm text-left border-collapse">
    <thead>
      <tr class="bg-gray-50/90 border-b border-gray-200">
        <th class="py-3 px-5 text-gray-500 font-semibold uppercase text-xs tracking-wider w-1/4">Aspect</th>
        <th class="py-3 px-5 text-gray-700 font-bold text-sm w-3/8">🌱 Vanilla JavaScript</th>
        <th class="py-3 px-5 text-emerald-800 font-bold text-sm w-3/8 bg-emerald-50/80 border-l border-emerald-100">▲ Next.js</th>
      </tr>
    </thead>
    <tbody class="divide-y divide-gray-100">
      <tr v-click class="hover:bg-gray-50/50 transition-colors">
        <td class="py-2.5 px-5 font-semibold text-gray-800">📄 Base HTML</td>
        <td class="py-2.5 px-5 text-gray-600">Written by hand (manual DOM)</td>
        <td class="py-2.5 px-5 font-semibold text-emerald-700 bg-emerald-50/40 border-l border-emerald-100">
          ✨ Generated automatically
        </td>
      </tr>
      <tr v-click class="hover:bg-gray-50/50 transition-colors">
        <td class="py-2.5 px-5 font-semibold text-gray-800">🧭 Routing</td>
        <td class="py-2.5 px-5 text-gray-600">Manual <code>if</code> per page</td>
        <td class="py-2.5 px-5 font-semibold text-emerald-700 bg-emerald-50/40 border-l border-emerald-100">
          📁 Folder name = URL route
        </td>
      </tr>
      <tr v-click class="hover:bg-gray-50/50 transition-colors">
        <td class="py-2.5 px-5 font-semibold text-gray-800">🖥️ Server Setup</td>
        <td class="py-2.5 px-5 text-gray-600">Configured by you (Express)</td>
        <td class="py-2.5 px-5 font-semibold text-emerald-700 bg-emerald-50/40 border-l border-emerald-100">
          ⚡ Zero-config, built-in
        </td>
      </tr>
      <tr v-click class="hover:bg-gray-50/50 transition-colors">
        <td class="py-2.5 px-5 font-semibold text-gray-800">➕ Add New Page</td>
        <td class="py-2.5 px-5 text-gray-600">Edit script + server routes</td>
        <td class="py-2.5 px-5 font-semibold text-emerald-700 bg-emerald-50/40 border-l border-emerald-100">
          📂 Create a folder &amp; <code>page.js</code>
        </td>
      </tr>
    </tbody>
  </table>
</div>

<div v-click class="mt-4 p-3.5 rounded-xl bg-gradient-to-r from-emerald-800 to-emerald-950 text-white text-center shadow flex items-center justify-center gap-3">
  <span class="text-xl">💡</span>
  <p class="m-0 text-sm font-medium tracking-wide">
    <strong>A framework provides the structure</strong>, so you can focus 100% on your content.
  </p>
</div>

</div>


---
class: flex flex-col
---

## Why Next.js? 🤔

<div class="my-auto">

<div class="card bolt text-xl p-8 [&_li]:mb-4">

- **The learning curve is easier than other technologies**
- **Optimized for speed and search engines**
- **File-system routing**
- **Frontend and backend in one project**
- **It runs on the server**

</div>

</div>

---
class: flex flex-col
---

## A friendly learning curve 📈

<div class="my-auto">

<p class="text-xs text-gray-600 mb-3">
  If you know <strong>HTML, CSS, and basic JavaScript</strong>, you already know 80% of Next.js.
</p>

<div class="grid grid-cols-2 gap-6 items-center">

<div>

<div class="text-xs font-semibold text-emerald-800 uppercase tracking-wider mb-2">📄 app/about/page.js</div>

```jsx
// app/about/page.js → /about
import Link from 'next/link';

export default function About() {
  return (
    <main>
      <h1>About Us</h1>
      <Link href="/">Back home</Link>
    </main>
  );
}
```

</div>

<div class="flex flex-col gap-2.5">

<div class="card p-3 text-xs leading-relaxed">
  <div class="font-bold text-emerald-800 mb-0.5">1. It's just a regular JS function</div>
  <span class="text-gray-600">No complex classes. A page is simply a JavaScript function returning your UI.</span>
</div>

<div class="card p-3 text-xs leading-relaxed">
  <div class="font-bold text-emerald-800 mb-0.5">2. It's the HTML you already know</div>
  <span class="text-gray-600">Write <code>&lt;main&gt;</code> and <code>&lt;h1&gt;</code> directly inside the function. No more tedious <code>innerHTML</code> or <code>createElement</code>.</span>
</div>

<div class="card p-3 text-xs leading-relaxed">
  <div class="font-bold text-emerald-800 mb-0.5">3. Familiar tags with superpowers</div>
  <span class="text-gray-600"><code>&lt;Link href="/"&gt;</code> works just like an <code>&lt;a&gt;</code> tag, but navigates instantly without reloading the browser.</span>
</div>

</div>

</div>

</div>

---
layout: two-cols-header
layoutClass: gap-12
---

## Optimized for speed and search engines ⚡

::left::

### Vanilla JavaScript

<p class="min-h-[44px] text-gray-700 leading-relaxed mb-3">
  The server sends an <strong>empty page</strong>. The browser must run JavaScript to build the HTML.
</p>

```html
<body>
  <!-- Empty container: no initial HTML -->
  <div id="app"></div>
  <script src="script.js"></script>
</body>
```

::right::

### Next.js

<p class="min-h-[44px] text-gray-700 leading-relaxed mb-3">
  The server sends the page <strong>already built</strong>. Cont~ent is visible to users and SEO (Search Engine Optimization) right away.
</p>

```html
<body>
  <h1>About Us</h1>
  <p>We build cool things.</p>
  <script src="..."></script>
</body>
```

---
class: flex flex-col
---

## File-system routing 📁

<div class="my-auto">

<div class="grid grid-cols-2 gap-6 items-start">

<div>

<div class="text-xs font-semibold text-emerald-800 uppercase tracking-wider mb-2">📁 Your project folders</div>

```
app/
├── 📄 page.js         →  /
├── 📁 about/
│   └── 📄 page.js    →  /about
├── 📁 contact/
│   └── 📄 page.js    →  /contact
└── 📁 blog/
    └── 📄 page.js    →  /blog
```

<div class="card bolt mt-3 text-xs leading-relaxed">

- A **folder** with `page.js` = a **new URL**
- No router file to edit, no manual configuration
- 404 error page handled automatically

</div>

</div>

<div>

<div class="text-xs font-semibold text-emerald-800 uppercase tracking-wider mb-2">🌐 The browser output</div>

<!-- Browser window mock -->
<div class="rounded-xl overflow-hidden shadow-md border border-gray-200/80 bg-white">
  <!-- Window Header -->
  <div class="bg-gray-100 px-3 py-2 border-b border-gray-200 flex items-center gap-2">
    <div class="flex gap-1.5">
      <div class="w-2.5 h-2.5 rounded-full bg-red-400"></div>
      <div class="w-2.5 h-2.5 rounded-full bg-yellow-400"></div>
      <div class="w-2.5 h-2.5 rounded-full bg-green-400"></div>
    </div>
    <!-- URL input -->
    <div class="flex-1 bg-white rounded-md px-2.5 py-1 text-xs text-gray-700 flex items-center shadow-inner border border-gray-200 font-mono">
      <span class="text-gray-400 mr-1 text-[11px]">🔒 localhost:3000</span>
      <span class="text-emerald-700 font-bold bg-emerald-100/70 px-1 rounded">/about</span>
    </div>
  </div>

  <!-- Window Content -->
  <div class="p-4 bg-white text-center">
    <span class="inline-block px-2 py-0.5 text-[10px] font-semibold text-emerald-800 bg-emerald-100 rounded-full mb-1">Live Page</span>
    <h3 class="text-lg font-bold text-gray-800 mb-1">About Us</h3>
    <p class="text-xs text-gray-500 m-0">Rendered from <code class="text-emerald-700">app/about/page.js</code></p>
  </div>
</div>

<div class="mt-3 p-3 rounded-xl bg-white shadow border border-emerald-900/10 text-xs text-gray-700 flex flex-col gap-1.5 font-mono">
  <div class="flex items-center justify-between">
    <span class="text-gray-600">📁 app/<strong>about</strong>/page.js</span>
    <span class="text-emerald-600 font-sans font-bold">➔</span>
    <span class="text-emerald-800 font-semibold">/about</span>
  </div>
  <div class="flex items-center justify-between">
    <span class="text-gray-600">📁 app/<strong>contact</strong>/page.js</span>
    <span class="text-emerald-600 font-sans font-bold">➔</span>
    <span class="text-emerald-800 font-semibold">/contact</span>
  </div>
</div>

</div>

</div>

</div>

---
class: flex flex-col
---

## Frontend and backend, one project 🧩

<div class="my-auto">

<div class="grid grid-cols-2 gap-x-6 gap-y-3 items-start">

<div class="text-xs font-semibold text-emerald-800 uppercase tracking-wider">📁 One folder, two worlds</div>
<div class="text-xs font-semibold text-emerald-800 uppercase tracking-wider">⚙️ The Backend Code (<code>route.js</code>)</div>

<div>

```
app/
├── 🎨 page.js        → Frontend (UI)
├── 🎨 about/
│   └── page.js     → Frontend (UI)
└── ⚙️ api/
    └── hello/
        └── route.js  → Backend (API)
```

</div>

<div>

```javascript
// app/api/hello/route.js  →  /api/hello

export async function GET() {
  return Response.json({
    message: 'Hello from the backend!'
  });
}
```

</div>

<div class="card bolt text-xs leading-relaxed">

- **`page.js`** = renders the UI (React)
- **`route.js`** = handles API requests (Node.js)

</div>

<div class="card bolt text-xs leading-relaxed">

- **No second server:** no Express or extra setup
- **One deploy:** frontend & backend live together

</div>

</div>

</div>

---
class: flex flex-col
---

## It runs on the server.

<div class="my-auto">

```tsx
// app/products/page.js →  runs on the server
export default async function Products() {
  const res = await fetch('https://api.example.com/products');
  const products = await res.json();

  return (
    <ul>
      {products.map((p) => (
        <li key={p.id}>{p.name}</li>
      ))}
    </ul>
  );
}
```

<div class="card bolt mt-4">

- **Faster for the user:** the data is fetched before the page arrives
- **Lighter for the device:** the server does the heavy work, not the phone
- **Safer:** passwords and API keys stay on the server, never in the browser
- **Better for the browser:** it receives the finished content

</div>

</div>
---
layout: center
class: text-center
---

# And one last reason... 🥁

<div class="w-16 h-1 bg-emerald-600 my-4 mx-auto"></div>

_Last but not least!_

---
layout: center
class: text-center
---

# It's free 💸

<div class="w-16 h-1 bg-emerald-600 my-4 mx-auto"></div>

**Open source** (MIT license). No fees, no licenses, no "contact sales".

_Student budget approved._ 🎓

---
layout: center
---


![Coding](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExa29ianRzengwd3p1OHdpdTNpZXg0MGI1cXR6MjJ5OHd5c2prN2k1cCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/1gdr2teAX3Rf5avTnB/giphy.gif)

---
layout: center
class: text-center
---

Questions ?

<img src="/sticker.png" class="h-50" />

---
layout: center
class: text-center
---

Thank you ✨

Gloria Rodriguez Fernandez 👩🏽‍💻