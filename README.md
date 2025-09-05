# CloudNexus: End-to-End DevOps Pipeline Implementation

![License](https://img.shields.io/badge/License-MIT-green.svg?style=flat-square)

**Complete implementation of a DevOps pipeline for a web application using modern practices: CI/CD, Infrastructure as Code, Kubernetes, and GitOps.**

## 📖 Огляд проекту

Цей проект демонструє повний цикл розгортання cloud-native додатку (Todo App) з використанням сучасного DevOps стеку. Метою є створення надійної, автоматизованої та безпечної pipeline від коду до продакшену.

**👨‍💻 Автор:** Ваше Ім'я \
**📧 Контакт:** [paul.antonenko.w@gmail.com](paul.antonenko.w@gmail.com) | [LinkedIn](https://www.linkedin.com/in/pavlo-antonenko/) \
**🚀 Live Demo:** _Додати посилання після розгортання_

---

## 🏗 Архітектура системи

_На цьому етапі архітектура знаходиться в стадії планування. Оновлю цю секцію після завершення наступних етапів._

### Заплановані компоненти:
1. **Джерело коду:** GitHub репозиторій з гілкуванням за стратегією GitFlow
2. **CI/CD:** GitHub Actions для збірки, тестування та сканування образів
3. **Реєстр образів:** DockerHub
4. **Інфраструктура (IaC):** AWS (EC2, VPC, S3), розгорнута за допомогою Terraform
5. **Контейнеризація:** Docker
6. **Оркестрація:** Kubernetes (k3s або Minikube для локального тестування)
7. **Моніторинг:** Prometheus/Grafana для збору метрик та візуалізації

---

## ⚙️ Технологічний стек

| Категорія | Технології |
|-----------|------------|
| **Cloud** | AWS (EC2, VPC, IAM, S3) |
| **Infrastructure as Code** | Terraform |
| **CI/CD** | GitHub Actions |
| **Containers** | Docker |
| **Orchestration** | Kubernetes |
| **Web Servers** | Nginx |
| **Programming** | Node.js, React |
| **Version Control** | Git, GitHub |

---

## 📂 Структура репозиторію (поточний стан)

devops-portfolio-project/
├── app/
│   ├── backend/
│   └── frontend/
├── infrastructure/
│   └── terraform/
├── kubernetes/
│   └── base/
├── .github/workflows/
└── README.md

---

## 🚀 Поточний статус

### ✅ Етап 0: Підготовка (Завершено)
- [x] Створено публічний GitHub репозиторій
- [x] Ініціалізовано структуру папок
- [x] Додано базовий код додатку (бекенд на Node.js/Express та фронтенд на React)
- [x] Налаштовано гілку `master`

### 🔄 Наступні етапи:
- [ ] Етап 1: Налаштування CI/CD з GitHub Actions
- [ ] Етап 2: Інфраструктура як код (IaC) з Terraform
- [ ] Етап 3: Контейнеризація з Docker
- [ ] Етап 4: Розгортання в Kubernetes
- [ ] Етап 5: Моніторинг та логування

---

## 🚀 Як запустити проект локально

Інструкції нижче дозволять вам запустити копію проекту на вашому локальному комп'ютері для розробки та тестування.

### Пререквізити:

Перед початком роботи переконайтеся, що на вашому комп'ютері встановлено:
*   **Node.js** (версія 16 або вище) - середовище виконання для JavaScript.
*   **npm** - менеджер пакетів, встановлюється разом з Node.js.
*   **Git** - для клонування репозиторію.

**Як перевірити?** Виконайте в терміналі:
```bash
   node --version
   npm --version
   git --version
```

###Кроки для запуску:
<details>
<summary>Клонуйте репозиторій:</summary>
  
```bash
   git clone https://github.com/ваш-юзернейм/ваш-репозиторій.git
   cd ваш-репозиторій
```
</details>
<details>
<summary>Запустіть бекенд (API сервер)</summary>
+ Відкрийте термінал і перейдіть в папку бекенду:

```bash
   cd app/backend
```
+ Встановіть залежності:

```bash
  npm install
```
+ Запустіть сервер:

```bash
  npm run dev
```
+ Сервер запуститься на порту `3000`:`http://localhost:3000`
</details>
<details>
<summary>Запустіть фронтенд (клієнтську частину):</summary>
+ Відкрийте новий термінал (щоб не зупиняти бекенд) і перейдіть в папку фронтенду:

```bash
  cd app/frontend
```
+ Встановіть залежності:

```bash
  npm install
```
+ Запустіть клієнт:

```bash
  npm run dev
```
+ Додаток автоматично відкриється в браузері на порту `5173`:`http://localhost:5173`
</details>

---

## 📊 Скріни роботи системи

<details>
<summary>Структура проекту в IDE</summary>
![Project Structure in IDE](docs/images/stage-0-ide-structure.png)
*Створена структура папок відповідає плану. Видно папки `app/backend`, `app/frontend`, `infrastructure/` та інші.*
</details>

<details>
<summary>Командний рядок з структурою</summary>
![Terminal Tree Command](docs/images/stage-0-terminal-tree.png)
*Вивід команди `tree`, що підтверджує логічну організацію файлів проекту.*
</details>

<details>
<summary>Працюючий додаток в браузері</summary>
![Local Application Running](docs/images/stage-0-app-running.png)
*Frontend-додаток (React) успішно запущено на `localhost:3000` і взаємодіє з бекендом (Node.js).*
</details>

<details>
<summary>Взаємодія фронтенду з бекендом</summary>
![Browser Network Tab](docs/images/stage-0-network-requests.png)
*Вкладка "Мережа" в інструментах розробника браузера показує успішні HTTP-запити з фронтенду на бекенд-API.*
</details>
