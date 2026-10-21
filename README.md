# CSDI Lab — Taiwan Internship Journey (2026intern)

A short, reusable **GitHub Pages** website for a 2–6-month visiting research internship at **National Taipei University of Technology (NTUT)**. Its focus is the student's personal journey: **research + learning + life in Taiwan + memories**. Designed to make an authentic, student-authored record that can support TEEP reporting/evaluation, without presenting a rigid research scorecard or inventing program requirements.

The homepage has exactly one link to **Browse regular meetings**, and **no separate Showcase page**. Research outputs, photographs, presentations, experiences and lessons are embedded in the **monthly journey**.

## What visitors see

- **Home:** an informal introduction and a month-by-month collection of highlights.
- **One page per month:** a more personal post combining lab activities, new skills and Taiwan experiences. Photos and captions are optional.
- **Looking back:** a short closing reflection on what the internship meant to the student.
- **Regular meetings:** a public list of meeting dates; clicking a date opens an **AES-GCM encrypted** HTML page which requires the meeting password.

The number of months is **not fixed**. Create entries only for the months actually spent in Taiwan; two entries make a two-month journey, six entries make a six-month journey.

## 1. Set up a new master template repository

**Suggested repository name:** `2026intern` (the name is only a suggestion, not a repository that has already been created).

1. Create `hendrisutrisno/2026intern` and upload **the extracted folder contents to the repository root**, preserving subfolders such as `.github/`, `docs/`, `meetings/`, `scripts/` and `_templates/`. Files should not be nested in an extra `2026intern-template/` folder on GitHub.
2. In **Settings > Secrets and variables > Actions > New repository secret**, add the secret `MEETING_PASSWORD` with value **`hope`** for **testing this public template only**.
3. In **Settings > Pages**, choose **GitHub Actions** for the deployment source. Do **not** select "Deploy from a branch"; this template encrypts notes during a workflow build.
4. Open **Actions > Publish intern journey > Run workflow**. Pushes to `main` also trigger a build automatically.
5. After successful deployment, open `https://hendrisutrisno.github.io/2026intern/`. The meeting list is at `/2026intern/meetings/`, and the sample encrypted meeting note is at `/2026intern/meetings/2026-10-21.html` (password `hope`).
6. In **Settings > General**, mark the master repo as a **Template repository** if students will copy it.

**Public-template disclosure:** the `meetings/2026-10-21.rst` file is a fictional demo and **visible in this public repository**. Password protection of the published HTML does **not** hide source files in a public repository. **Never put confidential meeting notes, research code or personal data in the public master template.**

## 2. Create a new private repository for each intern

Use **Use this template** and create a **private** repo such as `2026mei`, `2026verin`, or `2026ahmad` under `hendrisutrisno` (short lowercase names avoid Pages path mismatches). Invite only the relevant intern and authorized lab supervisors.

Edit `docs/_config.yml`:

```yaml
url: "https://hendrisutrisno.github.io"
baseurl: "/2026mei"   # must match the repository name exactly

demo: false
intern:
  name: "Mei"
  program: "TEEP Research Internship"
  lab: "CSDI Lab"
  university: "National Taipei University of Technology"
  home_university: "Home university"
  country: "Country"
  stay: "November 2026–February 2027"
  focus: "Human motion analysis and machine learning"
  summary: "A short introduction in my own words."
  looking_back: "My final reflections; update this near the end of my stay."
```

Delete or replace both demonstration monthly entries (`docs/_months/2026-10.md`, `docs/_months/2026-11.md`) and the fictional meeting note (`meetings/2026-10-21.rst`). Set **a new secret** `MEETING_PASSWORD` on the copied repository (secrets are **not copied** when creating from a template). Enable **GitHub Actions** under Pages and run the workflow.

GitHub Pro can publish a **public Pages website** from a **private** source repository under your personal account. The private `.rst` sources and `research/` code stay in the private GitHub repository; only approved `docs/` content and encrypted HTML are published.

**Do not use `hope` for actual confidential meeting notes.** It is intentionally a weak demonstration password. Use a long, random, unique password per intern and share it through an approved private channel. Since published ciphertext can be copied and attacked offline, weak passwords are unsafe.

## 3. Add monthly highlights (the main TEEP evidence)

Each month, copy `docs/_templates/monthly-highlight.md` to a new file in `docs/_months/` such as `2026-12.md`.

The **required** fields for each monthly card are:

| Field | Purpose | Recommended writing style |
| --- | --- | --- |
| `title`, `date` | When it happened, with a personal title | "Little wins and unexpected discoveries" |
| `research` | One meaningful lab/research activity or contribution | 1–2 sentences, concrete and honest |
| `taiwan` | A Taiwan experience, social interaction or cultural observation | 1–2 sentences in the student's own voice |
| `learning` | One insight, skill, challenge overcome, or changed perspective | 1–2 sentences reflecting development |

The **optional** fields are `tags`, `cover`, `cover_alt`, `cover_caption`, and `gallery` with image captions. The Markdown body below `---` can contain any additional story, reflection, approved resource, demo, or photograph.

Suggested minimum cadence: **one post per month**, approximately 150–300 words across the short summaries and longer narrative, with at least one meaningful research-learning point and one Taiwan-life experience. This is a **lab documentation guideline**, not a claim about formal TEEP rules.

**For TEEP evaluation:** keep each entry student-authored, date-stamped, and specific. Focus on experiences and growth. A genuine note about a difficult experiment or learning Taiwanese public transportation is often more informative than a generic promotional paragraph. Include approved evidence (photos, workshop attendance, presentation snapshots or outputs) where available, but do not invent results or activities.

### Add photographs

1. Upload approved JPEG/PNG/WebP photos to `docs/assets/photos/`.
2. In the month's front matter, optionally add:

```yaml
cover: /assets/photos/first-month.jpg
cover_alt: Student at the NTUT campus entrance during orientation
cover_caption: First week in Taipei

gallery:
  - src: /assets/photos/outing.jpg
    alt: Group photo at a cultural event with everyone's permission
    caption: My first weekend exploring Taiwan with friends
```

The homepage automatically shows the cover photo for the month; if no cover is provided it uses an illustration. The month page displays any additional gallery photographs. You **do not need** a separate showcase section.

**Photos and privacy:** Obtain consent before publishing photographs of other people, and do not publish private student information, raw research data, confidential experiments, copyrighted materials without permission, or restricted partner data.

### Add or remove months

The home page reads Jekyll's `months` collection and **sorts by the `date` field**. No need to edit `docs/index.md` for each new month. The site makes no assumption about whether the student stays two, four, or six months.

Each month is also a standalone HTML story at `/journey/YYYY-MM/` (derived from the file name); the homepage links to it with **Read the full story**.

## 4. Regular meetings: same private `.rst` workflow

1. Copy `_templates/regular-meeting.rst` to **`meetings/YYYY-MM-DD.rst`**, using the actual meeting date.
2. Submit the short note at least **24 hours before each scheduled supervision meeting**. Fill in the final decisions after the meeting.
3. Commit the `.rst` file. The workflow then updates the public date list and encrypts HTML using the `MEETING_PASSWORD` Actions secret.
4. The public index is `https://hendrisutrisno.github.io/2026mei/meetings/`; a meeting link looks like `/2026mei/meetings/2026-12-02.html`.

The `.rst` source must stay **outside `docs/`**, in the private `meetings/` directory. Store internal research code, notebooks, experiment results, and confidential files outside `docs/`, for example in a `research/` directory in the student's **private** repo.

If a workflow fails due to a missing `MEETING_PASSWORD` secret, add it and re-run. The build is intentionally designed to fail instead of publishing unencrypted meeting content.

## 5. Repository layout

```text
2026intern/
├── .github/workflows/publish.yml      # GitHub Actions -> Pages
├── docs/                              # only this subtree is published
│   ├── _config.yml                     # intern's profile, URL, final reflection
│   ├── index.md                        # homepage with automatically generated monthly cards
│   ├── _months/                        # one Markdown file per month (2–6 months)
│   ├── _layouts/                       # default and month page layouts
│   ├── _data/meetings.json             # generated list of meeting dates
│   ├── _templates/monthly-highlight.md # starter file, not published
│   ├── assets/
│   │   ├── style.css
│   │   └── photos/                     # approved public photos only
│   └── meetings/index.html             # public meeting-date list
├── meetings/                          # PRIVATE in each student repo
│   └── 2026-10-21.rst                  # sample only; replace or remove
├── research/                           # PRIVATE source code/notebooks/results
├── scripts/build_protected_meetings.py
├── _templates/regular-meeting.rst
└── README.md
```

## 6. Security and accuracy notes

- The Actions secret `MEETING_PASSWORD` is used **only at build time**, not stored in public HTML or in the `.rst` source.
- Each meeting HTML page uses AES-256-GCM encryption and PBKDF2-HMAC-SHA256 key derivation with a random salt, as in the graduate template. A static password does **not** provide user-specific access control or revocation.
- Publishing the source repo publicly reveals all source notes regardless of the password. Real intern repos must be private if they contain protected data.
- A Pages website published from a private repo is still **public**. Monthly stories and approved photos should be treated as public records.
- The sample monthly entries are labeled **SAMPLE STORY** and are fictional placeholders, not evidence of a real internship. Delete them before any reporting.
- This is a lab-managed portfolio for showcasing an intern's development; it is **not a replacement** for any official TEEP submission or attendance/finance forms.
