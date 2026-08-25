<div align="center">

<a href="https://port-tau-azure.vercel.app">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=20&duration=3000&pause=800&color=0EA5E9&center=true&vCenter=true&width=560&lines=5%2B+years+building+for+web+%26+mobile;React+%E2%80%A2+Next.js+%E2%80%A2+Vue+%E2%80%A2+React+Native+%E2%80%A2+Flutter;Micro+Frontend+%E2%80%A2+Module+Federation+%E2%80%A2+Monorepo;Node.js+%E2%80%A2+Laravel+%E2%80%A2+MySQL+%E2%80%A2+MongoDB" alt="Typing SVG" />
</a>

<br/>

<a href="https://port-tau-azure.vercel.app">
  <img src="https://img.shields.io/badge/Portfolio-Live%20Site-0EA5E9?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" />
</a>
<a href="https://www.linkedin.com/in/angga-w-a45b0111a/">
  <img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
</a>
<a href="mailto:anggawika18@gmail.com">
  <img src="https://img.shields.io/badge/Email-Say%20Hello-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" />
</a>
<img src="https://komarev.com/ghpvc/?username=AnggaWikaNugraha&style=for-the-badge&color=0EA5E9&label=PROFILE+VIEWS" alt="Profile views" />

</div>

---

## 🧭 About Me

> Software Engineer with **5+ years** of experience building scalable web and mobile applications.

- 🏗️ I build **frontend and fullstack** products — from pixel-accurate UI to the API and database behind it.
- ⚛️ Web with **React.js, Next.js, Vue.js**; mobile with **React Native** and **Flutter**.
- 🧩 I design **Micro Frontend** architectures — splitting a large app into independently built and deployed modules with **Module Federation**.
- 🛠️ Backend with **Node.js** and **Laravel**, backed by **MySQL** and **MongoDB** (Mongoose ODM, Eloquent ORM).
- ✨ I care about **clean, maintainable, scalable, and accessible** code.
- 🤝 Comfortable collaborating with cross-functional teams in **Agile Scrum** environments.
- 🌐 More projects and technical details → **[port-tau-azure.vercel.app](https://port-tau-azure.vercel.app)**

---

## 🧩 Micro Frontend Architecture

Instead of one giant SPA, I split the frontend into **independent modules** — each with its own repo/workspace, its own build, its own deploy, and its own team ownership. A thin **Host (Shell)** composes them at runtime.

```mermaid
graph TD
    U[User] --> H["🏠 HOST / SHELL<br/>routing · auth · layout · shared state"]
    H -->|remoteEntry.js| A["🧾 mf-dashboard<br/>React + Vite"]
    H -->|remoteEntry.js| B["💳 mf-transaction<br/>React + Webpack 5"]
    H -->|remoteEntry.js| C["👤 mf-account<br/>Vue 3"]
    H --> D["📦 shared-ui<br/>design system · hooks · utils"]
    A --> D
    B --> D
    C --> D
```

### How the modules are split

| Module | Type | Responsibility |
| :--- | :--- | :--- |
| **Host / Shell** | Container | App routing, authentication, global layout, error boundary, loading remotes |
| **Feature Remotes** | Remote | One business domain per module (dashboard, transaction, account) — built & deployed on its own |
| **shared-ui** | Library | Design system components, theme tokens, shared hooks & helpers |
| **shared-core** | Library | API client, auth session, event bus, TypeScript contracts |

### Key principles

- **Independent deploy** — a remote ships without rebuilding the host or any sibling module.
- **Shared singletons** — `react`, `react-dom`, and the router are declared as `singleton: true` so only one instance lives in the browser.
- **Contract-first** — every remote exposes a typed public surface; nothing reaches into another module's internals.
- **Runtime isolation** — a failing remote is caught by the shell's error boundary instead of taking down the whole app.
- **Graceful fallback** — lazy loading with `<Suspense>` + skeleton while `remoteEntry.js` is fetched.

### 🛠️ Tools I use

| Layer | Tools |
| :--- | :--- |
| **Composition** | Webpack 5 Module Federation · `@originjs/vite-plugin-federation` · Next.js Multi Zones · single-spa |
| **Monorepo** | Nx · Turborepo · pnpm workspaces |
| **Shared UI** | Storybook · Tailwind CSS · Radix UI · design tokens |
| **Cross-module state** | Zustand · Redux Toolkit · Custom Event Bus (`CustomEvent` / pub-sub) |
| **Contracts & quality** | TypeScript · ESLint · Prettier · Vitest / Jest · Playwright |
| **Delivery** | Docker · GitHub Actions · Vercel — one pipeline per remote |

<details>
<summary><b>📄 Example — Module Federation config</b></summary>

```js
// host/webpack.config.js
new ModuleFederationPlugin({
  name: 'host',
  remotes: {
    dashboard: 'dashboard@https://dashboard.example.com/remoteEntry.js',
    transaction: 'transaction@https://transaction.example.com/remoteEntry.js',
  },
  shared: {
    react: { singleton: true, requiredVersion: '^18.0.0' },
    'react-dom': { singleton: true, requiredVersion: '^18.0.0' },
  },
});

// remote/webpack.config.js
new ModuleFederationPlugin({
  name: 'dashboard',
  filename: 'remoteEntry.js',
  exposes: { './DashboardApp': './src/App' },
  shared: { react: { singleton: true }, 'react-dom': { singleton: true } },
});
```

</details>

---

## 🧰 Tech Stack

<div align="center">

**Languages**

<img src="https://skillicons.dev/icons?i=ts,js,dart,php,html,css" height="46" alt="Languages" />

**Frontend & Mobile**

<img src="https://skillicons.dev/icons?i=react,nextjs,vue,nuxtjs,flutter,tailwind,redux" height="46" alt="Frontend and Mobile" />

**Architecture & Build**

<img src="https://skillicons.dev/icons?i=webpack,vite,nx,pnpm,babel,jest" height="46" alt="Architecture and Build" />

**Backend & Database**

<img src="https://skillicons.dev/icons?i=nodejs,express,laravel,mysql,mongodb,prisma" height="46" alt="Backend and Database" />

**Tools & Platform**

<img src="https://skillicons.dev/icons?i=git,github,docker,figma,postman,vercel,vscode" height="46" alt="Tools" />

</div>

---

## 🚀 Featured Work

| Project | Description | Stack |
| :--- | :--- | :--- |
| **[Personal Portfolio](https://port-tau-azure.vercel.app)** | Fullstack portfolio with public site + protected admin dashboard, drag-to-reorder content, image uploads, and a language lab. | `Next.js 15` `MySQL` `JWT` `Cloudinary` |
| **Project Two** | Short one-line description of what it does and why it matters. | `React Native` `Node.js` `MongoDB` |
| **Project Three** | Short one-line description of what it does and why it matters. | `Vue.js` `Laravel` `MySQL` |

<div align="center">
  <a href="https://port-tau-azure.vercel.app">
    <img src="https://img.shields.io/badge/See%20all%20projects%20%E2%86%92-Visit%20Portfolio-0EA5E9?style=for-the-badge" alt="See all projects" />
  </a>
</div>

---

## 🤝 Let's Build Something

<div align="center">

Open to interesting frontend & fullstack work — feel free to reach out.

<a href="mailto:anggawika18@gmail.com">
  <img src="https://img.shields.io/badge/Gmail-anggawika18@gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white" alt="Gmail" />
</a>
<a href="https://www.linkedin.com/in/angga-w-a45b0111a/">
  <img src="https://img.shields.io/badge/LinkedIn-Angga%20Wika-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn" />
</a>
<a href="https://github.com/AnggaWikaNugraha">
  <img src="https://img.shields.io/badge/GitHub-AnggaWikaNugraha-181717?style=flat-square&logo=github&logoColor=white" alt="GitHub" />
</a>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0EA5E9,50:1E3A8A,100:0F172A&height=120&section=footer" width="100%" />

</div>
