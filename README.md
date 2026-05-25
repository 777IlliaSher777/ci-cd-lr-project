# React + TypeScript + Vite


This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Oxc](https://oxc.rs)
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/)

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default defineConfig([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...

      // Remove tseslint.configs.recommended and replace with this
      tseslint.configs.recommendedTypeChecked,
      // Alternatively, use this for stricter rules
      tseslint.configs.strictTypeChecked,
      // Optionally, add this for stylistic rules
      tseslint.configs.stylisticTypeChecked,

      // Other configs...
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x'
import reactDom from 'eslint-plugin-react-dom'

export default defineConfig([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...
      // Enable lint rules for React
      reactX.configs['recommended-typescript'],
      // Enable lint rules for React DOM
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```
# ci-cd-lr-project

# CI/CD Automation for React + Vite  

## Опис

У межах лабораторної роботи було реалізовано повноцінний CI/CD pipeline для frontend-застосунку, створеного за допомогою React та Vite.

Для автоматизації процесів розробки було використано GitHub Actions. Реалізовано автоматичну перевірку якості коду, створення релізів, оновлення документації та deploy застосунку на GitHub Pages.

---

## Використані технології

- React
- Vite
- GitHub Actions
- GitHub Pages
- Node.js
- Chuck Norris API

### Середовище розробки

- Visual Studio Code
- Git
- GitHub

---

## Реалізовані Workflow

### 1. CI Workflow (`ci.yml`)

Workflow запускається при:
- `push`
- `pull_request`

Основні функції:
- встановлення залежностей;
- запуск lint;
- запуск тестів;
- build проєкту.

У випадку помилки lint, tests або build pipeline завершується зі статусом `failed`.

---

### 2. Deploy Workflow (`deploy.yml`)

Workflow автоматично:
- збирає React + Vite проєкт;
- створює production build;
- виконує deploy на GitHub Pages.

Після успішного deploy застосунок стає доступним за публічним URL.

---

### 3. Release Workflow (`release.yml`)

Workflow автоматично:
- генерує номер нової версії;
- створює git tag;
- створює GitHub Release;
- отримує випадковий Chuck Norris joke через API;
- оновлює README.md.

---

## Формування версії

Номер версії формується автоматично через:

```yaml
v1.0.${{ github.run_number }}
```

При кожному запуску workflow номер збільшується.

---

## Інтеграція Chuck Norris API

Для інтеграції зовнішнього API використовується:

https://api.chucknorris.io/

Під час виконання workflow автоматично виконується HTTP-запит через `curl`, після чого випадковий joke додається у:
- README.md
- Release notes

---

## Deploy на GitHub Pages

Deploy виконується автоматично через GitHub Actions після успішного проходження CI pipeline.

---

<!-- RELEASE-INFO-START -->
## Latest Release Info

- Version: v1.0.5
- PR Title: Manual push to main
- Chuck Norris Joke: Chuck Norris's dog doesn't know who's a good boy.
<!-- RELEASE-INFO-END -->

---

## Висновок

У результаті лабораторної роботи було реалізовано сучасний CI/CD pipeline для frontend-проєкту з автоматизацією перевірки коду, створення релізів, оновлення документації та deploy застосунку.