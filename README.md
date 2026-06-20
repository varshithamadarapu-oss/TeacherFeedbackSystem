# Teacher Feedback System

A fully static, GitHub Pages-compatible web application for collecting and reviewing student feedback on teachers. No server, no database, no build step required — everything runs in the browser using localStorage.

---

## Features

- **10 Teachers** with Indian names and subjects
- **Star ratings (1–5)** across 3 categories per teacher:
  - Teaching Quality
  - Doubt Clarification
  - Command on Subject
- **Comments** section per teacher (optional text feedback)
- **Feedback submission** with validation
- **Summary page** showing:
  - Aggregated average ratings per category
  - Visual progress bars
  - All submitted comments
  - Overall stats (total submissions, teachers rated, global average)
- **Filter** summary by individual teacher
- **100% offline** — data stored in browser localStorage
- **Responsive** — works on mobile, tablet, and desktop

---

## Project Structure

```
teacher-feedback-system/
├── index.html              ← Main feedback form page
├── summary.html            ← Summary / results page
├── css/
│   └── style.css           ← All styles
├── js/
│   ├── data.js             ← Teachers data + localStorage layer
│   ├── app.js              ← Feedback form logic
│   └── summary.js          ← Summary page logic
├── .github/
│   └── workflows/
│       └── deploy.yml      ← GitHub Actions auto-deploy workflow
└── README.md               ← This file
```

---

## How to Deploy on GitHub Pages

### Method 1 — GitHub Actions (Recommended, fully automatic)

1. **Create a new GitHub repository**
   - Go to [github.com/new](https://github.com/new)
   - Give it a name (e.g. `teacher-feedback-system`)
   - Set it to **Public**
   - Click **Create repository**

2. **Upload all project files**
   - Click **"uploading an existing file"** on the repository page
   - Drag and drop **all files and folders** from this project
   - Make sure the folder structure is preserved (css/, js/, .github/)
   - Click **Commit changes**

3. **Enable GitHub Pages**
   - Go to your repository → **Settings** → **Pages** (left sidebar)
   - Under **Source**, select **GitHub Actions**
   - Click **Save**

4. **Your site is live!**
   - GitHub will automatically run the deploy workflow
   - Your URL will be: `https://<your-username>.github.io/<repo-name>/`
   - Check the **Actions** tab to monitor the deployment (takes ~1 minute)

---

### Method 2 — Manual Upload (No GitHub Actions)

1. **Create a new GitHub repository** (same as above, set to Public)

2. **Upload all project files** (same as above)

3. **Enable GitHub Pages manually**
   - Go to repository → **Settings** → **Pages**
   - Under **Source**, select **Deploy from a branch**
   - Branch: `main`, Folder: `/ (root)`
   - Click **Save**

4. **Your site is live!**
   - URL: `https://<your-username>.github.io/<repo-name>/`
   - May take 2–5 minutes for the first deployment

---

### Method 3 — Git Command Line

```bash
# 1. Initialize git in this folder
git init

# 2. Add all files
git add .

# 3. Commit
git commit -m "Initial commit: Teacher Feedback System"

# 4. Add your GitHub repo as remote (replace with your URL)
git remote add origin https://github.com/<your-username>/<repo-name>.git

# 5. Push to GitHub
git push -u origin main

# 6. Then enable GitHub Pages in repository Settings → Pages
```

---

## How Data Works

- All feedback is saved to **browser localStorage** under the key `teacher_feedback_v1`
- Data persists across page refreshes and browser sessions
- Data is **local to each browser** — it is not shared or synced anywhere
- Use the **"Clear All Data"** button on the Summary page to reset everything

---

## Customisation

### Change teacher names or subjects
Edit `js/data.js` — update the `TEACHERS` array:

```js
const TEACHERS = [
  { id: 1, name: "Your Teacher Name", subject: "Your Subject", initials: "YT" },
  // ...
];
```

### Change rating categories
Edit the `CATEGORIES` array in `js/data.js`:

```js
const CATEGORIES = [
  { key: "teaching",           label: "Teaching Quality"   },
  { key: "doubtClarification", label: "Doubt Clarification" },
  { key: "commandOnSubject",   label: "Command on Subject"  },
];
```

### Change colours / theme
Edit `css/style.css` — update the CSS variables at the top:

```css
:root {
  --navy: #1a2f5e;      /* Primary colour */
  --accent: #e8a020;    /* Highlight / gold */
  /* ... */
}
```

---

## Browser Support

Works in all modern browsers: Chrome, Firefox, Safari, Edge.
Requires JavaScript to be enabled.
