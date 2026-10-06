# Label Generator API

Backend для проекта генерации штрихкодов и этикеток. API построен на Node.js, Express и MongoDB с Mongoose; авторизация использует JWT.

## Связанные проекты

- Frontend: [Frontend-label-generator-website](https://github.com/BekowDev/Frontend-label-generator-website)
- Live demo: [frontend-label-generator-website.vercel.app](https://frontend-label-generator-website.vercel.app)
- Backend: [API-for-barcode-label-generator](https://github.com/BekowDev/API-for-barcode-label-generator)

> Live demo фронтенда — самостоятельное демо генератора. Его шаблоны, штрихкоды и экспорт работают на стороне браузера; для локального демо подключение этого API не требуется.

## Требования

- Node.js и npm
- Доступная MongoDB (локальная или MongoDB Atlas)

## Установка и запуск

```bash
npm install
```

Создайте в корне проекта файл `.env`:

```env
PORT=3000
DB_URL=mongodb://127.0.0.1:27017/label-generator
token_key=replace-with-a-long-random-secret
```

Замените адрес MongoDB и секрет JWT своими значениями. Не публикуйте `.env` и не добавляйте реальные секреты в репозиторий.

Запуск с автоматической перезагрузкой:

```bash
npm run dev
```

Обычный запуск:

```bash
npm start
```

Сервер подключается к MongoDB и слушает порт из `PORT`. API доступно с префиксом `/api`.

## Основные маршруты

| Метод | Путь | Назначение |
| --- | --- | --- |
| `POST` | `/api/signUp` | Регистрация пользователя |
| `POST` | `/api/signIn` | Вход пользователя |
| `POST` | `/api/updateUsername` | Изменение имени пользователя; требуется авторизация |
| `DELETE` | `/api/deleteUser` | Удаление пользователя; требуется авторизация |
| `POST` | `/api/labels` | Создание этикетки; требуется авторизация |
| `POST` | `/api/getLabels` | Получение этикеток пользователя; требуется авторизация |
| `POST` | `/api/changeLabels` | Изменение этикетки; требуется авторизация |
| `POST` | `/api/deleteLabels` | Удаление этикеток; требуется авторизация |

Для защищённых маршрутов передавайте JWT, выданный при входе, в заголовке авторизации согласно реализации middleware проекта.
