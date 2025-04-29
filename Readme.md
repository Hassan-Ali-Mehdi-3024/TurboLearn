
# 📚 TurboLearn

An AI-powered web application to create, manage, and practice flashcards, quizzes, and notes from uploaded PDFs or chat-based input.

---

## 🌐 Live Deployment

- **Frontend:** [Link to Frontend](https://mcqsbank-frontend.onrender.com)
- **Backend:** [Link to Backend](https://django-based-mcq-app.onrender.com)

---

## ⚙️ Tech Stack

| Layer     | Tech                        |
|-----------|-----------------------------|
| Frontend  | React (Vite + TypeScript)   |
| Backend   | Django + Django REST Framework (DRF) |
| Auth      | JWT (via `djangorestframework-simplejwt`) |
| Deployment| Render (Static + Web Service) |
| AI        | OpenAI / Gemini + Langchain |
| File Uploads | PDF via REST API |
| Styling   | ShadCN + Tailwind CSS       |

---

## 📁 Frontend Folder Structure (`/TurboLearn-Frontend/src`)

The frontend uses a modular and scalable structure organized by functionality:

```
src/
├── components/       # Reusable UI components (buttons, forms, modals, loaders, etc.)
├── config/           # Configuration files (e.g., API base URL, environment constants)
├── contexts/         # Global app state managed via React Context (e.g., AuthContext)
├── hooks/            # Custom React hooks for modular logic (e.g., useAuth)
├── lib/              # Utility functions and external integrations
├── pages/            # Top-level route views (Login, Dashboard, Flashcards, etc.)
├── router/           # Route definitions and layout logic
├── services/         # Centralized API communication (auth, learning, chat, etc.)
```

---

## 🗺️ Frontend Pages & Routes

| Path             | Page               | Description                        |
|------------------|--------------------|------------------------------------|
| `/`              | Dashboard          | User’s main view after login       |
| `/login`         | Login              | JWT-based login                    |
| `/signup`        | Signup             | New user registration              |
| `/upload`        | Upload             | Upload PDF to generate notes       |
| `/notes`         | Notes              | View generated notes               |
| `/notes/:id`     | NoteView           | Single note in detail              |
| `/flashcards`    | Flashcards         | Flashcard list                     |
| `/flashcards/:id`| FlashcardView      | Single flashcard                  |
| `/quizzes`       | Quizzes            | List of generated quizzes          |
| `/quizzes/:id`   | QuizView           | Quiz detail / attempt              |
| `/chat`          | Chat               | AI-based chat/assistant            |
| `/forgot-password`| ForgotPassword    | Reset password page                |
| `*`              | NotFound           | 404 page                           |

---

## 🔐 Authentication Flow

- `AuthContext.tsx` provides global state for login/signup/logout
- `authService.ts` handles:
  - `POST /api/token/` → Login
  - `POST /api/register/` → Signup
  - `GET /api/check-username/` → Username check
- JWT tokens are stored in localStorage
- Auth status checked on app mount

---

## 🔄 API Integration (Services)

### `/services/auth.ts`
- Handles login, registration, logout
- Stores JWT and user data in `localStorage`

### `/services/learning.ts`
- Upload PDFs
- Retrieve notes and flashcards

### `/services/chatService.ts`
- Sends user input to LLM (OpenAI/Gemini)
- Receives structured content (flashcards, notes, quiz)

### `/services/quizService.ts`
- Fetches available quizzes
- Submits answers

---

## 🧠 AI Features

- **LangChain + OpenAI/Gemini** used to:
  - Parse and summarize PDF content
  - Generate flashcards
  - Create quizzes
- Backend uses `/upload-pdf/` to accept PDF → sends content to LLM → returns structured data

---

## 📦 Environment Variables

### Frontend (Render Static Site)
```
VITE_API_URL=https://django-based-mcq-app.onrender.com
```

### Backend (Render Web Service)
```
SECRET_KEY=...
DEBUG=False
ALLOWED_HOSTS=...
GOOGLE_API_KEY=...
OPENAI_API_KEY=...
```

---

## 🚀 Deployment (Render)

- Frontend: Render Static Site from `/TurboLearn-Frontend/`
  - Build Command: `npm install && npm run build`
  - Publish Directory: `dist`
- Backend: Python Web Service from `/TurboLearn-Backend/`
  - Start Command: `gunicorn quizapp.wsgi:application --bind 0.0.0.0:$PORT`

---

## 📌 Future Improvements

- Add user profile dashboard
- Allow user-uploaded question answers
- Admin panel for content moderation
- Export notes/flashcards to PDF
- Analytics dashboard (quizzes attempted, scores, etc.)

---

## 👨‍💻 Developed By

**Technologistics**  
AI-powered solutions for better learning and automation.

- 🌐 Website: [www.technologistics.pk](https://technologistics.pk/)
- 📧 Email: contact@technologistics.pk
- 📞 Contact: +92 327 4320706
- 🔗 LinkedIn: [linkedin.com/company/technologistics-pk/](https://www.linkedin.com/company/technologistics-pk/)
- 📸 Instagram: [@technologistics.pk](https://www.instagram.com/technologistics.pk/)
