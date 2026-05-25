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

- Version: v1.0.4
- PR Title: Manual push to main
- Chuck Norris Joke: The 1951 UFO sighting was actually a man hole cover kicked by Chuck Norris.
<!-- RELEASE-INFO-END -->

---

## Висновок

У результаті лабораторної роботи було реалізовано сучасний CI/CD pipeline для frontend-проєкту з автоматизацією перевірки коду, створення релізів, оновлення документації та deploy застосунку.