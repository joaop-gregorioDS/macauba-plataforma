<div align="center">

# 🌿 Plataforma Macaúba · Soberania Energética & Bioeconomia

**Dossiê Interativo de Bioeconomia e Engenharia Front-end de Alta Performance**

[![Deploy Vercel](https://img.shields.io/badge/Deploy-Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://plataforma-macauba.vercel.app)
[![Deploy Netlify](https://img.shields.io/badge/Deploy-Netlify-00C7B7?style=for-the-badge&logo=netlify&logoColor=white)](https://plataforma-macauba.netlify.app)
[![Deploy GitHub Pages](https://img.shields.io/badge/Deploy-GitHub_Pages-222222?style=for-the-badge&logo=githubpages&logoColor=white)](https://joaop-gregoriods.github.io/macauba-plataforma/)
[![Deploy Firebase](https://img.shields.io/badge/Deploy-Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)](https://plataforma-macauba.web.app)

<br />

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/pt-BR/docs/Web/HTML)
[![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS_v3-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![JavaScript](https://img.shields.io/badge/Vanilla_JS_ES6+-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
[![Canvas API](https://img.shields.io/badge/Canvas_2D_API-EA4335?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/pt-BR/docs/Web/API/Canvas_API)
[![Lenis Scroll](https://img.shields.io/badge/Lenis-Smooth_Scroll-7928CA?style=flat-square)](https://lenis.darkroom.engineering/)
[![Architecture](https://img.shields.io/badge/Architecture-Zero--Bundler_SPA-blue?style=flat-square)](#-arquitetura-de-software--decisões-de-engenharia)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

</div>

---

> 🚀 **Acesse a Aplicação em Produção (Live Deploys):**
> * **Ambiente Vercel (Edge CDN):** [plataforma-macauba.vercel.app](https://plataforma-macauba.vercel.app)
> * **Ambiente Netlify:** [plataforma-macauba.netlify.app](https://plataforma-macauba.netlify.app)
> * **Ambiente GitHub Pages:** [joaop-gregoriods.github.io/macauba-plataforma](https://joaop-gregoriods.github.io/macauba-plataforma/)
> * **Ambiente Google Firebase:** [plataforma-macauba.web.app](https://plataforma-macauba.web.app)

---

## 🎯 O que o Projeto Resolve?

A **Plataforma Macaúba** é uma interface digital e simulador analítico concebido para tangibilizar o impacto macroeconômico e ambiental da cultura da palmeira Macaúba (*Acrocomia aculeata*) no Brasil. 

O projeto soluciona o desafio de **comunicação de dados técnicos complexos** (bioenergia, biocombustíveis avançados como SAF e HVO, transição energética e créditos de carbono) através de uma **experiência editorial imersiva e interativa**.

### Principais Capacidades da Aplicação:
- **Simulador Paramétrico em Tempo Real:** Recálculo dinâmico de faturamento bruto, produção de SAF/HVO, farelo proteico e biocarvão com base na variação de hectares produtivos (de 10M a 100M ha).
- **Matriz de Balanço de Massa e Coprodutos:** Visualização da conversão de biomassa por tonelada processada em biorrefinarias de alta tecnologia.
- **Dossiê Estratégico Multissetorial:** Análise aprofundada dos eixos de Defesa & Soberania, Segurança Alimentar, Petroquímica Verde e Mercado Voluntário de Carbono.

---

## 🏗️ Arquitetura de Software & Decisões de Engenharia

O projeto foi intencionalmente arquitetado sob o paradigma **Zero-Bundler / High-Performance Static SPA**, demonstrando domínio profundo sobre os padrões nativos da Web (Web APIs, Render Pipeline, DOM e Layout Engine) sem a sobrecarga de abstrações desnecessárias.

```
┌─────────────────────────────────────────────────────────────────┐
│                       INDEX.HTML (SPA Core)                     │
├────────────────────────┬────────────────────────────────────────┤
│     Camada Visual      │   - Tipografia Editorial Fluida        │
│    (CSS & Tokens)      │   - Tailwind Utility CSS via CDN       │
│                        │   - CSS Custom Properties (--amber,etc)│
├────────────────────────┼────────────────────────────────────────┤
│   Motor Gráfico 2D     │   - Canvas Particle System             │
│     (Canvas API)       │   - Decoupled requestAnimationFrame    │
│                        │   - Vector Math & Viewport Responsive  │
├────────────────────────┼────────────────────────────────────────┤
│   Motor de Interação   │   - Lenis Inertial Scroll Engine       │
│    (JS Engine & IO)    │   - IntersectionObserver (Zero-Jank)   │
│                        │   - Reactive State Engine (Simulador)  │
└────────────────────────┴────────────────────────────────────────┘
```

### 1. Desempenho & Render Pipeline (Zero-Jank)
* **Canvas 2D Particle Engine:** O fundo dinâmico utiliza um loop desacoplado via `requestAnimationFrame` que recalcula posições vetoriais de partículas estocásticas com `devicePixelRatio` adaptativo, minimizando *paint flashing* e mantendo taxa constante de 60/120 FPS.
* **Inertial Smooth Scrolling (Lenis):** Implementação de suavização de rolagem com interpolação linear (`lerp: 0.1`) e suporte a *smooth wheel*, elevando a ergonomia da navegação para o padrão Awwwards.
* **Intersection Observer API:** O acionamento de animações de entrada (*reveal*) e preenchimento de barras analíticas é computado de forma assíncrona na thread do navegador através de observadores de interseção (`threshold: 0.05`, `rootMargin: '0px 0px -50px 0px'`), eliminando gargalos de *scroll-listening* na Main Thread.

### 2. Estado Reativo e Manipulação do DOM
* **Motor do Simulador Econômico:** Implementado em Vanilla JS puro utilizando funções puras de cálculo (`calcOutput(hectares)`) que realizam mutações pontuais no DOM via `textContent` e `toLocaleString('pt-BR')`, evitando re-renderizações completas de árvores de nós.
* **Acessibilidade & Semântica:** Estrutura construída sobre tags semânticas (`<main>`, `<section>`, `<article>`, `<header>`, `<footer>`), suporte a leitores de tela com atributos `aria-hidden` e modais acessíveis com `role="dialog"` e gerenciamento de foco.

### 3. Pipeline de Distribuição Multicloud (CI/CD)
O repositório é configurado para entrega contínua multicloud através de *Git Webhooks*:
* **Vercel & Netlify:** Builds atômicos disparados a cada `git push` na branch `master` com distribuição global via Edge CDN.
* **GitHub Pages:** Deploy automatizado nativo direto do branch principal.
* **Firebase Hosting:** Arquitetura de contingência hospedada nos servidores globais da Google Cloud Platform.

---

## 📂 Estrutura do Repositório

```bash
macauba-plataforma/
├── index.html         # Ponto de entrada, estrutura semântica, estilos e scripts
├── 404.html           # Página de fallback e roteamento estático
├── firebase.json      # Configurações de hospedagem e cache do Google Firebase
├── .firebaserc        # Mapeamento do projeto no Firebase CLI
├── .gitignore         # Regras de exclusão de artefatos locais
└── README.md          # Documentação técnica de engenharia
```

---

## 💻 Como Rodar o Projeto Localmente

Por ser uma aplicação nativa de alta performance que não exige etapas de compilação (*zero build step*), a execução local é instantânea.

### Pré-requisitos
- Um navegador moderno (Chrome, Edge, Firefox, Safari).
- (Opcional) Node.js ou extensão de servidor estático.

### Passo a Passo

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/joaop-gregorioDS/macauba-plataforma.git
   cd macauba-plataforma
   ```

2. **Execute um servidor HTTP local:**
   
   *Opção A — Usando Python:*
   ```bash
   python -m http.server 8080
   ```

   *Opção B — Usando Node.js (`npx serve`):*
   ```bash
   npx serve .
   ```

   *Opção C — Usando VS Code:*
   - Instale a extensão **Live Server** e clique em **Go Live** no canto inferior direito.

3. **Acesse no seu navegador:**
   ```
   http://localhost:8080
   ```

---

## 👨‍💻 Autor & Contato Profissional

Desenvolvido por **João P. Gregório** — Desenvolvedor Front-end & Engenheiro de Software.

- **E-mail:** [joaop.gregorio@outlook.com](mailto:joaop.gregorio@outlook.com)
- **WhatsApp:** [+55 11 98388 1984](https://wa.me/5511983881984)
- **GitHub:** [github.com/joaop-gregorioDS](https://github.com/joaop-gregorioDS)
- **Repositório do Projeto:** [joaop-gregorioDS/macauba-plataforma](https://github.com/joaop-gregorioDS/macauba-plataforma)

---

<div align="center">
  <sub>© 2026 · Projeto de Portfólio Técnico · Desenvolvido com foco em performance e precisão de engenharia.</sub>
</div>
