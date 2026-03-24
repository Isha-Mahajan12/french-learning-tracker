# 🇫🇷 Daily Workflow — French Learning Tracker

Your 15-minute daily routine to keep pace with fast-track French learning.

---

## What You Do Each Day

### Step 1 — Upload your PPTX to Claude (2 min)
Open a new Claude conversation and paste this prompt, then attach your `.pptx` file:

---

**PASTE THIS PROMPT INTO CLAUDE:**

```
You are my French learning assistant. I've uploaded today's French lesson PowerPoint.

Please extract and structure ALL content from the slides into a JSON file using EXACTLY this schema:

{
  "meta": {
    "lesson_number": <number>,
    "title": "<lesson title from slides>",
    "date": "<today's date YYYY-MM-DD>",
    "topic": "<1-sentence topic summary>",
    "duration_minutes": <estimated study time>,
    "difficulty": "<beginner|intermediate|advanced>"
  },
  "vocabulary": [
    { "french": "", "english": "", "notes": "" }
  ],
  "verbs": [
    {
      "infinitive": "",
      "meaning": "",
      "conjugations": {
        "je": "", "tu": "", "il/elle": "", "nous": "", "vous": "", "ils/elles": ""
      },
      "notes": "",
      "examples": ["French sentence — English translation"]
    }
  ],
  "grammar": [
    { "title": "", "explanation": "" }
  ],
  "key_phrases": [
    { "french": "", "english": "", "context": "" }
  ],
  "cultural_notes": [
    { "title": "", "content": "" }
  ],
  "practice_exercises": [
    {
      "type": "fill_in_the_blank|translate|multiple_choice",
      "instruction": "",
      "items": [{ "prompt": "", "answer": "" }]
    }
  ],
  "extra_sections": [
    {
      "label": "<section name>",
      "icon": "✨",
      "content": "<text content OR leave empty if using items>",
      "items": ["<list item 1>", "<list item 2>"]
    }
  ]
}

Rules:
- Extract EVERY piece of content from the slides — don't skip anything
- If the slides have sections not covered by the schema above, put them in extra_sections
- For verbs, always provide full conjugation tables (all 6 forms)
- For vocabulary, add helpful notes about usage, pronunciation, or exceptions
- Generate 3-5 practice exercises based on the lesson content
- Keep all French text exactly as written (with accents)
- Output ONLY valid JSON, no markdown code blocks, no extra text

My lesson number today is: [REPLACE WITH LESSON NUMBER]
```

---

### Step 2 — Save the JSON (3 min)
1. Copy the JSON output from Claude
2. Create a new file in your repo: `lessons/lesson-XX.json` (e.g. `lesson-02.json`)
3. Paste and save

### Step 3 — Register the lesson (1 min)
Open `docs/index.html` and find this section near the top of the `<script>`:

```javascript
const LESSONS = [
  'lessons/lesson-01.json',
  // Add your new lesson here:
  'lessons/lesson-02.json',
];
```

Uncomment or add the new lesson file path.

### Step 4 — Commit and push (2 min)
```bash
git add .
git commit -m "Add lesson 02: [topic]"
git push
```

GitHub Pages will update in ~30 seconds.

### Step 5 — Review (7 min)
Open your GitHub Pages site and review today's lesson:
- Read through vocabulary
- Test yourself on verb conjugations
- Do the practice exercises (use "Show answer" to check)
- Read grammar notes
- Check cultural context

---

## First-Time Setup

### 1. Create the GitHub repo

```bash
git init french-learning-tracker
cd french-learning-tracker
```

Copy in the project files:
```
french-learning-tracker/
├── docs/
│   └── index.html       ← the website
├── lessons/
│   └── lesson-01.json   ← your first lesson
├── DAILY_WORKFLOW.md    ← this file
└── README.md
```

### 2. Push to GitHub

```bash
git add .
git commit -m "Initial setup"
git remote add origin https://github.com/YOUR_USERNAME/french-learning-tracker.git
git branch -M main
git push -u origin main
```

### 3. Enable GitHub Pages

1. Go to your repo on GitHub
2. **Settings → Pages**
3. Source: **Deploy from a branch**
4. Branch: `main`, Folder: `/docs`
5. Click Save

Your site will be live at: `https://YOUR_USERNAME.github.io/french-learning-tracker`

---

## Extra Sections Claude Will Auto-Detect

When Claude processes your PPTX, it will automatically identify and extract into `extra_sections`:

- 📊 Listening/dialogue transcripts
- 🗂 Topic-specific word groups (numbers, colours, days of week, etc.)
- 🔗 Pronunciation rules
- 📐 Sentence structure patterns
- 🔁 Review/revision content from previous lessons
- 🎵 Songs, mnemonics, or memory aids

---

## Tips

- **Always give Claude the lesson number** in your prompt so the JSON is correctly numbered
- If the slides are in French only, tell Claude: *"Slides are in French — translate vocabulary and explanations to English"*
- If Claude misses content, follow up with: *"You missed [section name] — please add it to the JSON"*
- For lessons with audio exercises, type out the dialogue/transcript manually into `extra_sections` after you receive the JSON
