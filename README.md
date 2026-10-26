# CSDI Lab — Taiwan Internship Journey (Template)

A ready-to-use website for intern visiting research interns at **National Taipei University of Technology (NTUT)**. It publishes your personal internship story — research, learning, life in Taiwan, and memories — as a clean, public website hosted on **GitHub Pages** for free.

> **New to GitHub?** Don't worry. This guide walks you through every step from zero.

---

## What the website looks like

| Page | What's on it |
|---|---|
| **Home** | Your introduction and a card for every two-week highlight |
| **Highlight page** | A longer personal post: lab activities, new skills, Taiwan experiences, optional photos |
| **Looking back** | A short reflection you add near the end of your stay |
| **Regular meetings** | A list of meeting dates; each one opens a password-protected page |

You add one highlight every two weeks. The homepage updates automatically — no code editing required.

---

## Step 0 — What you need before starting

- A **GitHub account** (free) — sign up at [github.com](https://github.com) if you don't have one.
- A computer with internet access.
- That's it. No programming knowledge needed for day-to-day use.

---

## Step 1 — Create your own repository from this template

> A **repository** (or "repo") is just a folder on GitHub that stores your files and tracks changes.

1. On the GitHub page for this template repo, click the green **"Use this template"** button near the top-right → then **"Create a new repository"**.
2. Set **Owner** to your GitHub username (e.g. `yourname`).
3. Set **Repository name** to something short and lowercase, like `2026yourname` (for example `2026mei` or `2026nael`). Avoid spaces or capital letters.
4. Set visibility to **Private** — this keeps your draft notes and meeting files hidden from the public.
5. Click **"Create repository"**. GitHub copies all the files for you.

---

## Step 2 — Fill in your profile (`docs/_config.yml`)

This file holds your name, university, and a few other details that appear on the homepage.

1. In your new repo, click on `docs/` → `_config.yml`.
2. Click the **pencil icon ✏️** in the top-right to edit the file.
3. Change the values below (leave everything else as-is):

```yaml
baseurl: "/2026yourname"   # ← change to your exact repository name

intern:
  name: "Your Full Name"
  program: "intern Research Internship"
  lab: "CSDI Lab"
  home_university: "Your Home University"
  country: "Your Country"
  stay: "October 2026 – January 2027"   # ← your actual dates
  focus: "What you are researching"
  summary: "A short introduction in your own words."
  looking_back: ""   # ← leave empty for now; fill in near the end
```

4. Scroll down and click **"Commit changes"** → **"Commit directly to the main branch"** → **"Commit changes"**.

> **Committing** just means saving your changes. Every save is recorded with a timestamp so you can always go back.

---

## Step 3 — Set the meeting password (secret)

Meeting notes are encrypted with a password so only the supervisor can read them after they are published.

1. In your repo, go to **Settings** (tab at the top) → **Secrets and variables** → **Actions** → **New repository secret**.
2. Name: `MEETING_PASSWORD`
3. Value: choose a long, random password and write it down somewhere safe. **Do not use `hope`** — that is only for testing.
4. Click **"Add secret"**.

> Secrets are hidden from everyone, including you, after you save them. The website build uses the secret automatically.

---

## Step 4 — Turn on the website (GitHub Pages)

1. In **Settings** → **Pages** (left sidebar).
2. Under **"Build and deployment"**, set Source to **GitHub Actions**.
3. Go to the **Actions** tab → click **"Publish intern journey"** → click **"Run workflow"** → **"Run workflow"** again.
4. Wait about 1–2 minutes. A green checkmark ✅ means success.
5. Your website is now live at:
   `https://yourusername.github.io/2026yourname/`

---

## Step 5 — Delete the sample highlights

The template includes two sample highlight files so you can see how the site looks. Delete them before your final submission.

1. Open `docs/_highlights/` in your repo.
2. Click on `2026-09-21.md` → click the **trash icon 🗑️** → **"Commit changes"**.
3. Repeat for `2026-10-05.md` and `2026-10-19.md`.

---

## Step 6 — Add a new highlight every two weeks ⭐

This is the main thing you do every two weeks throughout your internship.

1. Open `docs/_templates/monthly-highlight.md` and copy its entire contents.
2. In `docs/_highlights/`, click **"Add file"** → **"Create new file"**.
3. Name the file using the **start date of that two-week period**, e.g.:
   - `2026-10-01.md` for Oct 1–14
   - `2026-10-15.md` for Oct 15–28
   - `2026-11-01.md` for Nov 1–14
4. Paste the copied template content and fill in the fields:

```yaml
---
title: "Your personal title for this highlight"
date: 2026-10-01        # ← start date of the two-week period (YYYY-MM-DD)
research: "One meaningful thing you did in the lab."
taiwan: "One experience from life in Taiwan."
learning: "One insight, skill, or change in perspective."
tags: ["tag1", "tag2"]
---

Write a longer story here if you want. Photos, reflections, anything goes.
```

5. Click **"Commit changes"** at the bottom. The homepage card appears automatically within a minute or two.

### Add photos to a highlight

1. Upload your photo to `docs/assets/photos/` (click **"Add file"** → **"Upload files"**).
2. Add these lines to the front matter (the `---` section) of your highlight file:

```yaml
cover: /assets/photos/your-photo.jpg
cover_alt: A short description of the photo
cover_caption: Caption shown on the page

gallery:
  - src: /assets/photos/another-photo.jpg
    alt: Description
    caption: Caption
```

> Always get consent before publishing photos of other people.

### Add or remove highlights

The homepage reads all files in `docs/_highlights/` and sorts them by `date`. To remove a card, just delete the file. You don't need to edit `docs/index.md` at all.

---

## Step 7 — Add a regular meeting note

Before each supervision meeting, create a private note that gets encrypted when the site is built.

1. Go to `_templates/regular-meeting.rst` → copy the content.
2. In the `meetings/` folder (not `docs/`), create a new file named after the meeting date: `meetings/2026-11-03.rst`.
3. Fill in the template — agenda, what you discussed, decisions made.
4. Commit the file. The build automatically encrypts it and adds the date to the public meeting list.
5. Share your `MEETING_PASSWORD` with your supervisor through a private channel (email, LINE, etc.).

> The meeting source files in `meetings/` stay private in your repo. Only the encrypted HTML is published.

### Add photos to a meeting note

Store photos in `meetings/assets/` (not in `docs/`). Reference them in the `.rst` file like this:

```rst
.. figure:: assets/2026-11-03-board.jpg
   :alt: Whiteboard sketch of the experiment design
   :width: 720px
   :align: center

   Notes from the whiteboard after the meeting.
```

Each image must be under 8 MB. The build embeds them directly into the encrypted page.

### Add math equations to a meeting note

You can write LaTeX math equations inside meeting notes:

- **Inline equation**: `:math:`E = mc^2``
- **Block equation**:

```rst
.. math::

   \mathbf{x}_{t+1} = A \mathbf{x}_t + B \mathbf{u}_t
```

The build renders math equations cleanly with MathJax once the note is unlocked.

---

## Repository layout

```text
2026yourname/
├── .github/workflows/publish.yml       # Runs automatically on every save — don't edit
├── docs/                               # ← Everything here becomes your public website
│   ├── _config.yml                     # Your name, university, dates (edit this first)
│   ├── index.md                        # Homepage layout (no need to edit)
│   ├── _highlights/                    # ← Add one .md file here every two weeks
│   ├── _layouts/                       # Page templates (no need to edit)
│   ├── _data/meetings.json             # Auto-generated meeting date list
│   ├── _templates/monthly-highlight.md # Copy this when adding a new highlight
│   ├── assets/
│   │   ├── style.css                   # Website styling (no need to edit)
│   │   └── photos/                     # Upload your public photos here
│   └── meetings/index.html             # Public meeting date list (auto-generated)
├── meetings/                           # ← PRIVATE meeting notes go here (.rst files)
│   └── assets/                         # Private meeting photos go here
├── research/                           # Private research code, notebooks, results
├── scripts/build_protected_meetings.py # Used by the build workflow
├── _templates/regular-meeting.rst      # Copy this when adding a meeting note
└── README.md                           # This file
```

---

## Troubleshooting

| Problem | What to check |
|---|---|
| Website not updating after a commit | Go to **Actions** tab — look for a red ❌. Click it to read the error. |
| Build fails with "MEETING_PASSWORD not found" | Go to Settings → Secrets → add the secret (Step 3). |
| Cards on homepage not showing | Make sure the file is in `docs/_highlights/` and the `date:` field is a valid `YYYY-MM-DD` date. |
| Photos not showing | Check that the file is in `docs/assets/photos/` and the path in front matter starts with `/assets/photos/`. |
| Meeting page asks for a password I don't know | Ask your supervisor — they should have the `MEETING_PASSWORD`. |
| Dark/light mode toggle missing or broken | You likely uploaded `docs/_site/` to GitHub. Delete that folder from GitHub — it should never be uploaded. GitHub Actions builds the site automatically. |

> **⚠️ Manual upload warning:** When dragging files to GitHub, `.gitignore` is ignored. Never upload these folders: `docs/_site/`, `docs/.jekyll-cache/`. Only upload: `.github/`, `docs/` *(minus `_site/` and `.jekyll-cache/` inside it)*, `meetings/`, `scripts/`, `_templates/`, `.gitignore`, `README.md`, `_config.yml`, `publish.yml`.

---

## Privacy and security notes

- Files in `docs/` are **always public** once the site is built, even from a private repo. Only put content you are comfortable sharing publicly.
- Meeting notes in `meetings/` stay private in your repo. The encrypted HTML is public, but unreadable without the password.
- **Never** put your actual password inside any file in the repo.
- The sample highlights are fictional placeholders. Delete them before any intern evaluation.
- This website is a personal portfolio record; it is **not a replacement** for any official intern attendance forms or submissions.
