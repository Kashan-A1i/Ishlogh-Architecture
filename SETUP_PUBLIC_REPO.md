# 🚀 Publishing the Showcase Repository

These steps turn `_showcase/` into its **own standalone Git repository** — with a brand-new history containing zero commits from the private Ishlogh repo — and push it to:

**https://github.com/Kashan-A1i/Ishlogh-Architecture**

> [!IMPORTANT]
> `_showcase/` is listed in the private repo's `.gitignore`, so the private repo will never track it, and the new repo inside it will never see the private repo's history.

---

## 0. Prerequisites

- The GitHub repo `Kashan-A1i/Ishlogh-Architecture` exists and is **public**.
  - Ideally create it **empty** (no README, license or `.gitignore`). If it already has files, see [Step 5](#5-if-the-remote-already-has-commits).
- Git is installed and you're authenticated to GitHub (HTTPS + credential manager, or SSH key).

---

## 1. Final privacy scan (from the private repo root)

**PowerShell (Windows):**
```powershell
cd K:\Ishlogh
# Should list ONLY .md, .svg, .png, .gif and .gitkeep files
Get-ChildItem -Recurse -Force _showcase | Where-Object { -not $_.PSIsContainer } | Select-Object FullName

# Should return NOTHING (this setup file is excluded because it contains the search patterns)
Get-ChildItem -Recurse -File _showcase -Exclude SETUP_PUBLIC_REPO.md | Select-String -Pattern 'SECRET_KEY\s*=|django-insecure|B2_APPLICATION_KEY\s*=|postgres://|AKIA|BEGIN .*PRIVATE KEY'
```

**Bash (macOS/Linux/Git Bash):**
```bash
cd /path/to/Ishlogh
find _showcase -type f
grep -rEn --exclude=SETUP_PUBLIC_REPO.md 'SECRET_KEY\s*=|django-insecure|B2_APPLICATION_KEY\s*=|postgres://|AKIA|BEGIN .*PRIVATE KEY' _showcase || echo "clean ✅"
```

Also confirm the private repo is ignoring the folder:
```bash
git check-ignore -v _showcase/README.md
# expected: .gitignore:<line>:_showcase/    _showcase/README.md
```

---

## 2. Initialize a fresh repository inside `_showcase/`

```bash
cd _showcase
git init -b main
```

> On Git older than 2.28 (no `-b` flag): `git init` then `git checkout -b main`.

Optionally set the identity used for this repo only:
```bash
git config user.name  "Kashan"
git config user.email "your-public-email@example.com"   # or your GitHub noreply address
```

---

## 3. Create the first commit

```bash
git add .
git status            # review: only README.md, ARCHITECTURE.md, ASSETS_CHECKLIST.md, SETUP_PUBLIC_REPO.md, assets/
git commit -m "docs: initial Ishlogh architecture showcase"
```

Verify the history is brand new (should show exactly **1** commit):
```bash
git log --oneline
```

---

## 4. Connect the public remote and push

**HTTPS:**
```bash
git remote add origin https://github.com/Kashan-A1i/Ishlogh-Architecture.git
git push -u origin main
```

**or SSH:**
```bash
git remote add origin git@github.com:Kashan-A1i/Ishlogh-Architecture.git
git push -u origin main
```

---

## 5. If the remote already has commits

If you created the GitHub repo with a README/license, the first push is rejected. Pick one:

**A — Replace the remote contents with the showcase (recommended for a fresh repo):**
```bash
git push -u origin main --force
```

**B — Keep the remote's files and merge them in:**
```bash
git pull origin main --allow-unrelated-histories --no-rebase
# resolve any conflicts (e.g. README.md), then:
git add .
git commit -m "merge remote initial files"
git push -u origin main
```

---

## 6. Polish the GitHub repo page

On **github.com/Kashan-A1i/Ishlogh-Architecture → ⚙ About** (gear icon on the right):

- **Description:** `Architecture & engineering showcase for Ishlogh — a Django-powered digital archive preserving oral folklore as text, audio and video.`
- **Website:** your live deployment URL
- **Topics:** `django` `python` `postgresql` `backblaze-b2` `s3` `folklore` `digital-archive` `cultural-heritage` `render` `system-design` `architecture`
- Pin the repository on your GitHub profile.

---

## 7. Updating the showcase later

```bash
cd K:\Ishlogh\_showcase      # or the bash path
# edit docs / add screenshots to assets/
git add .
git commit -m "docs: add screenshots and demo gif"
git push
```

> [!CAUTION]
> Never run `git add` for `_showcase` from the **private** repo root, and never add the private repo as a remote of the showcase repo (or vice versa). The two repositories must stay completely independent.
