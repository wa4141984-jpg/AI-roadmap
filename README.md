# 🧭 AI Learning Roadmap Generator

A beginner-friendly web app that creates a **personalised learning roadmap** for any field or skill. You choose a topic, your skill level, how long you can study and how many hours per day. Google Gemini then writes a complete plan with stages, projects, free resources and a weekly schedule.

Built with **Python**, **Streamlit** and the **Google Gemini API**.

---

## ✨ Features

- Modern Streamlit dashboard with a sidebar input form
- Inputs: field, skill level, learning time, daily study hours, optional goal
- AI-generated roadmap with 12 sections:
  introduction, prerequisites, learning stages, Python libraries and tools, projects, free resources, YouTube channels and documentation, weekly schedule, practice exercises, final portfolio project, career opportunities and next steps
- Expandable sections (`st.expander`)
- Loading spinner while the AI works
- Download the roadmap as **Markdown (.md)** or **Text (.txt)**
- Reset button
- Simple error messages for: empty input, missing or invalid API key, quota limit, no internet, empty AI answer and unexpected errors
- API key stored safely in Streamlit secrets (never in the code)

## 🛠 Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main language |
| Streamlit | Web interface |
| Google Gemini API (`google-genai` SDK) | AI roadmap generation |
| Pandas | Summary table of the user's choices |
| NumPy | Study-hour and stage-week calculations |
| GitHub | Code storage |
| Streamlit Community Cloud | Free hosting |
| Claude AI | Code generation and review |

## 📁 Project Structure

```
ai-learning-roadmap-generator/
├── app.py                  # The complete application
├── requirements.txt        # Python dependencies
├── README.md               # This file
├── .gitignore              # (you create it) keeps secrets out of GitHub
└── .streamlit/
    └── secrets.toml        # (you create it) your API key – NEVER upload this
```

## ⚙️ Installation

You need **Python 3.9 or newer**.

```bash
# 1. Get the project (after you upload it to GitHub, or copy the folder)
git clone https://github.com/YOUR-USERNAME/ai-learning-roadmap-generator.git
cd ai-learning-roadmap-generator

# 2. Create and activate a virtual environment (recommended)
python -m venv venv

# Windows:
venv\Scripts\activate
# macOS / Linux:
source venv/bin/activate

# 3. Install the libraries
pip install -r requirements.txt
```

## 🔑 How to Get a Gemini API Key

1. Open **Google AI Studio**: <https://aistudio.google.com/>
2. Sign in with your Google account.
3. Click **Get API key** (left menu), then **Create API key**.
4. Copy the key and keep it private. Do not share it or post it on GitHub.

> Google's free tier has usage limits. If you reach them, wait a while and try again.

## 🔒 How to Configure the API Key (Secrets)

### Local computer

1. Create a folder named `.streamlit` inside the project folder.
2. Inside it, create a file named `secrets.toml`.
3. Add this line (use your own key):

```toml
GEMINI_API_KEY = "paste-your-key-here"
```

Optional – choose a different model:

```toml
GEMINI_MODEL = "gemini-3.8-flash"
```

### Streamlit Community Cloud

1. Open your deployed app → **Settings** → **Secrets**.
2. Paste the same lines in the box and click **Save**.

## ▶️ Run the App Locally

```bash
streamlit run app.py
```

Your browser opens at `http://localhost:8501`.

## 🤖 How to Change the Gemini Model

The app uses `gemini-3.8-flash` by default. Google retires old models from time to time, so you may need to change the name later. You have two options:

1. **Secrets (easiest):** add `GEMINI_MODEL = "new-model-name"` to your secrets.
2. **Code:** edit the line `DEFAULT_MODEL = "gemini-3.8-flash"` near the top of `app.py`.

Find current model names here: <https://ai.google.dev/gemini-api/docs/models>
Check retirement dates here: <https://ai.google.dev/gemini-api/docs/deprecations>

## 🐙 Upload the Project to GitHub

1. Create a file named `.gitignore` with this content:

```
.streamlit/secrets.toml
venv/
__pycache__/
*.pyc
```

2. Create a new **empty repository** on <https://github.com> (for example `ai-learning-roadmap-generator`).
3. In your project folder run:

```bash
git init
git add .
git commit -m "Initial commit: AI Learning Roadmap Generator"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/ai-learning-roadmap-generator.git
git push -u origin main
```

4. Open the repository on GitHub and confirm that `secrets.toml` is **not** there.

## ☁️ Deploy on Streamlit Community Cloud

1. Go to <https://share.streamlit.io> and sign in with GitHub.
2. Click **Create app** (or **New app**) and choose your repository.
3. Set **Branch** to `main` and **Main file path** to `app.py`.
4. Open **Advanced settings → Secrets** and paste:

```toml
GEMINI_API_KEY = "paste-your-key-here"
```

5. Click **Deploy**. After a few minutes your app has a public link.

## 🧯 Common Errors and Solutions

| Message or problem | What it means | Solution |
|---|---|---|
| "No Gemini API key was found" | The secret is missing | Add `GEMINI_API_KEY` to `.streamlit/secrets.toml` (local) or to the Secrets box (Cloud). Restart the app. |
| "Your Gemini API key looks invalid…" | Wrong, expired or restricted key | Create a new key in Google AI Studio and update the secret. |
| "The free usage limit (quota) has been reached" | Too many requests | Wait a few minutes, or check your limits in Google AI Studio. |
| "The model '…' was not found" | The model name is wrong or retired | Change the model name (see "How to Change the Gemini Model"). |
| "Could not reach the Gemini service" | No internet or a network block | Check your connection, VPN or firewall, then try again. |
| "The Gemini service is busy…" | Temporary problem on Google's side | Try again in a minute. |
| "The AI returned an empty answer" | The answer was blocked or empty | Rephrase the field or goal and try again. |
| "Please enter a field or domain" | The field box is empty | Type a topic such as `Data Science`. |
| `ModuleNotFoundError: No module named 'google'` | Libraries are not installed | Activate your virtual environment and run `pip install -r requirements.txt`. |
| `StreamlitSecretNotFoundError` | No secrets file | Create `.streamlit/secrets.toml` as shown above. |
| Cloud app still shows old behaviour | Old version is cached | Click **Reboot app** in the Streamlit Cloud menu. |

## ⚠️ Notes

- AI answers can contain mistakes. The app asks Gemini not to invent links, but always check resources yourself.
- The study-hour estimate assumes **6 study days per week**.
- Never commit your API key to GitHub. If you do, delete the key in Google AI Studio and create a new one.

## 📄 License

Free to use for learning and education. Add a license file (for example MIT) if you want to share the project publicly.# AI-roadmap
