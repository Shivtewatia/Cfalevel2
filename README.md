# CFA Level 2 — Study Dashboard

Live dashboard that reads your `progress.csv` and shows subject completion, weekly plan, and mock schedule. Auto-deploys to GitHub Pages on every push.

---

## Setup (one-time, ~10 minutes)

### Step 1 — Create your GitHub repository

1. Go to [github.com](https://github.com) → Sign in (or create a free account)
2. Click the **+** icon top-right → **New repository**
3. Name it: `cfa-dashboard`
4. Set it to **Public** (required for free GitHub Pages)
5. Leave everything else default → Click **Create repository**

---

### Step 2 — Upload the files

On your new empty repository page, click **uploading an existing file**

Upload ALL of these files maintaining the folder structure:
```
index.html
progress.csv
.github/
  workflows/
    deploy.yml
```

**Important:** GitHub's web uploader needs you to drag the `.github` folder. If it doesn't work, use GitHub Desktop (see Step 2b below).

**Step 2b — Using GitHub Desktop (easier):**
1. Download [GitHub Desktop](https://desktop.github.com) → Install
2. File → Clone Repository → Your `cfa-dashboard` repo → Choose a local folder
3. Copy all the files (index.html, progress.csv, .github folder) into that local folder
4. In GitHub Desktop: you'll see the files listed → Add a commit message like "Initial setup" → Click **Commit to main** → Click **Push origin**

---

### Step 3 — Enable GitHub Pages

1. In your repository → click **Settings** (top tab)
2. Left sidebar → **Pages**
3. Under "Source" → Select **GitHub Actions**
4. Save

---

### Step 4 — Update the CSV URL in index.html

Open `index.html` and find this line near the top of the `<script>` section:

```javascript
const CSV_URL = './progress.csv';
```

Replace it with your raw GitHub URL:

```javascript
const CSV_URL = 'https://raw.githubusercontent.com/YOUR_USERNAME/cfa-dashboard/main/progress.csv';
```

Replace `YOUR_USERNAME` with your actual GitHub username.

Save and push (commit + push in GitHub Desktop).

---

### Step 5 — Your live URL

After the first push, GitHub Actions will deploy your site. It takes about 2 minutes.

Your dashboard will be live at:
```
https://YOUR_USERNAME.github.io/cfa-dashboard
```

The Actions tab in your repo shows the deployment status.

---

## Updating your progress (daily workflow)

### From anywhere (phone or any computer) — GitHub web editor:
1. Go to your GitHub repo → click `progress.csv`
2. Click the pencil icon (Edit)
3. Change blank cells to `Done` or `Half`
4. Click **Commit changes**
5. Dashboard updates automatically in ~1 minute

### From your laptop (Excel/Sheets workflow):
1. Open `progress.csv` in Excel or Google Sheets
2. Update the Class / Reading / Notes / QBank columns:
   - Type `Done` when complete
   - Type `Half` for half-done
   - Leave blank for not started
3. Save as CSV (keep the filename `progress.csv`)
4. Open GitHub Desktop → you'll see the changed file
5. Write a commit message → **Commit to main** → **Push origin**
6. Dashboard updates in ~1 minute

---

## CSV column rules

| Value | Meaning |
|-------|---------|
| `Done` | Fully completed (scores 100%) |
| `Half` | Half done (scores 50%) |
| *(blank)* | Not started (scores 0%) |

**Do not change** the LM numbers, Subject names, or Title column — these are used to match rows to the plan.

---

## Files explained

| File | Purpose |
|------|---------|
| `index.html` | The entire dashboard (HTML + CSS + JS in one file) |
| `progress.csv` | Your progress data — edit this to update the dashboard |
| `.github/workflows/deploy.yml` | Tells GitHub to auto-deploy on every push |

---

## Troubleshooting

**Dashboard shows "Could not load progress.csv"**
→ Make sure you updated `CSV_URL` in index.html with your GitHub username

**GitHub Pages not showing up**
→ Check Settings → Pages → Source is set to "GitHub Actions"
→ Check the Actions tab — look for any red X errors

**CSV not updating the dashboard**
→ Make sure you're editing the file in the `main` branch
→ Hard-refresh the page (Ctrl+Shift+R on Windows, Cmd+Shift+R on Mac)

---

*Built for CFA L2 August 2026 exam.*
