## 🚀 Try It Out!

🆕 [Try it here](https://screenshottocode.com) (bring your own OpenAI key - **your key must have access to GPT-4 Vision. See [FAQ](#%EF%B8%8F-faqs) section below for details**). Or see [Getting Started](#-getting-started) below for local install instructions.

## 🌟 Recent Updates

- Dec 7 - 🔥 🔥 🔥 View a history of your edits, and branch off them
- Nov 30 - Dark mode, output code in Ionic (thanks [@dialmedu](https://github.com/dialmedu)), set OpenAI base URL
- Nov 28 - 🔥 🔥 🔥 Customize your stack: React or Bootstrap or TailwindCSS
- Nov 23 - Send in a screenshot of the current replicated version (sometimes improves quality of subsequent generations)
- Nov 21 - Edit code in the code editor and preview changes live thanks to [@clean99](https://github.com/clean99)
- Nov 20 - Paste in a URL to screenshot and clone (requires [ScreenshotOne free API key](https://screenshotone.com?via=screenshot-to-code))
- Nov 19 - Support for dark/light code editor theme - thanks [@kachbit](https://github.com/kachbit)
- Nov 16 - Added a setting to disable DALL-E image generation if you don't need that
- Nov 16 - View code directly within the app
- Nov 15 - You can now instruct the AI to update the code as you wish. It is helpful if the AI messed up some styles or missed a section.

## 🛠 Getting Started

The app has a React/Vite frontend and a FastAPI backend. You will need an OpenAI API key with access to the GPT-4 Vision API.

Run the backend (I use Poetry for package management - `pip install poetry` if you don't have it):

```bash
cd backend
echo "OPENAI_API_KEY=sk-your-key" > .env
poetry install
poetry shell
poetry run uvicorn main:app --reload --port 7001
```

Run the frontend:

```bash
cd frontend
yarn
yarn dev
```

Open http://localhost:5173 to use the app.

If you prefer to run the backend on a different port, update VITE_WS_BACKEND_URL in `frontend/.env.local`

For debugging purposes, if you don't want to waste GPT4-Vision credits, you can run the backend in mock mode (which streams a pre-recorded response):

```bash
MOCK=true poetry run uvicorn main:app --reload --port 7001
```

## Configuration

* You can configure the OpenAI base URL if you need to use a proxy: Set OPENAI_BASE_URL in the `backend/.env` or directly in the UI in the settings dialog

## Docker

If you have Docker installed on your system, in the root directory, run:

```bash
echo "OPENAI_API_KEY=sk-your-key" > .env
docker-compose up -d --build
```

The app will be up and running at http://localhost:5173. Note that you can't develop the application with this setup as the file changes won't trigger a rebuild.