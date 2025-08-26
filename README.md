# Mishel Lanka Tours (React + Vite)

A fast, SEO‑friendly travel website for Sri Lanka tours built with **React**, **Vite**, **React Router**, and **Tailwind CSS**.

> This README replaces the default Vite template and documents how to run, build, deploy, and contribute to the project.

---

## ✨ Features

* ⚡ **Vite + React** app with HMR for instant dev feedback
* 🗺️ **Tour pages & gallery** with responsive layouts
* 🚦 **Client routing** via React Router
* 🎨 **Tailwind CSS** utility‑first styling
* 🔍 **SEO basics**: meta tags, canonical, robots.txt, sitemap.xml
* 🧹 **ESLint + Prettier** for consistent code
* 📷 Local & remote image handling

---

## 🧱 Tech Stack

* **Frontend:** React 18/19 (see notes), Vite
* **Routing:** React Router
* **Styles:** Tailwind CSS, AOS (optional), Lucide icons
* **Linting/Format:** ESLint, Prettier
* **Deployment:** Netlify / Vercel

---

## 📂 Project Structure (typical)

```
mishel-lanka-tours/
├─ public/
│  ├─ favicon.ico
│  ├─ robots.txt
│  └─ sitemap.xml
├─ src/
│  ├─ assets/               # images, icons
│  ├─ components/           # Navbar, Footer, Cards, etc.
│  ├─ pages/                # Home, About, Packages, Gallery, Contact, TourDetails
│  ├─ routes/               # Router config (optional)
│  ├─ styles/               # Tailwind base (optional)
│  ├─ main.jsx
│  └─ App.jsx
├─ index.html
├─ package.json
├─ tailwind.config.js
├─ postcss.config.js
├─ .eslintrc.cjs
├─ .prettierrc
└─ README.md
```

---

## ✅ Prerequisites

* **Node.js** ≥ 18.18 (LTS recommended)
* **npm** ≥ 9 or **pnpm/yarn**

Check versions:

```bash
node -v
npm -v
```

---

## 🚀 Getting Started (Development)

1. **Install dependencies**

   ```bash
   npm install
   # or pnpm install / yarn
   ```
2. **Run the dev server**

   ```bash
   npm run dev
   ```
3. Open the printed **local URL** (usually `http://localhost:5173`).

---

## 🏗️ Build & Preview

```bash
# Production build
npm run build

# Serve the dist build locally for testing
npm run preview
```

The compiled site lives in `dist/`.

---

## 🧹 Quality: Linting & Formatting

```bash
# Lint (ESLint)
npm run lint

# Format (Prettier)
npm run format
```

> Tip: enable your editor’s ESLint & Prettier extensions and **format on save**.

---

## 🔐 Environment Variables

Create a `.env` (or `.env.local`) at the project root:

```
VITE_SITE_URL=https://mishellankatours.com
VITE_GA_ID=G-XXXXXXXXXX     # (optional) Google Analytics 4
```

Only variables prefixed with `VITE_` are exposed to the client.

---

## 🌐 SEO Setup

* **`index.html`** contains the base `<title>`, meta description, and canonical.
* **`public/robots.txt`**

  ```txt
  User-agent: *
  Allow: /
  Sitemap: https://mishellankatours.com/sitemap.xml
  ```
* **`public/sitemap.xml`**

  * Update with your live URLs (Home, About, Packages, Gallery, Contact, Tour Details)
* Use descriptive alt text for images and meaningful page titles (React Helmet or per‑route `<title>` updates if needed).

---

## 🛣️ Routing (example)

```jsx
import { createBrowserRouter, RouterProvider } from 'react-router-dom';
import App from './App';
import Home from './pages/Home';
import About from './pages/About';
import Packages from './pages/Packages';
import Gallery from './pages/Gallery';
import Contact from './pages/Contact';
import TourDetails from './pages/TourDetailsPage';

const router = createBrowserRouter([
  {
    path: '/',
    element: <App />,
    children: [
      { index: true, element: <Home /> },
      { path: 'about', element: <About /> },
      { path: 'packages', element: <Packages /> },
      { path: 'gallery', element: <Gallery /> },
      { path: 'contact', element: <Contact /> },
      { path: 'tour/:slug', element: <TourDetails /> },
    ],
  },
]);

export default function Routes() {
  return <RouterProvider router={router} />;
}
```

---

## 🖼️ Assets & Images

* Place static assets in `public/` or import via `src/assets`.
* Prefer modern formats (WebP/AVIF) with fallback JPG/PNG when needed.
* Keep images reasonably compressed for page speed.

---

## ☁️ Deployment

### Netlify

1. **New Site from Git** → pick repo
2. **Build command:** `npm run build`
3. **Publish directory:** `dist`
4. Add environment variables in **Site settings → Build & deploy → Environment**

### Vercel

1. **Import Project** → select repo
2. **Framework preset:** Vite
3. **Build Command:** `npm run build`
4. **Output Directory:** `dist`

> For client‑side routing, enable **SPA fallback**:
>
> * Netlify: add `_redirects` with `/*  /index.html  200`
> * Vercel: set a rewrite to `/index.html` for all routes

---

## 🧰 Common Issues

* **React 19 vs library peer deps**
  If you see errors like:

  ```
  ERESOLVE unable to resolve dependency tree
  peer react "^16 || ^17 || ^18" from some-library
  ```

  Options:

  1. Use React 18 for maximum compatibility
  2. Or install with legacy peer deps (temporary):

     ```bash
     npm i --legacy-peer-deps
     ```
  3. Or find a React‑19‑compatible alternative (e.g., replace `react-helmet-async` with a compatible meta solution or use React 18).

* **Images not loading in production**
  Make sure you reference assets correctly. Assets in `public/` are served from root (`/logo.svg`). Imported assets are hashed by Vite.

* **404s on refresh**
  Configure SPA fallback (see Deployment section).

---

## 🤝 Contributing

1. Create a feature branch: `git checkout -b feat/awesome-thing`
2. Commit with conventional messages: `feat(gallery): add lightbox`
3. Push and open a PR.

---

## 📝 Scripts (package.json)

```json
{
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "lint": "eslint .",
    "format": "prettier --write ."
  }
}
```

---

## 📄 License

This project is proprietary to Mishel Lanka Tours unless a license is added. Contact the owner for reuse permissions.

---

## 📬 Contact

* **Website:** [https://mishellankatours.com](https://mishellankatours.com)
* **Location:** Sri Lanka
