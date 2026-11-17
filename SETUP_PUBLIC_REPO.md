# Publishing & Updating the Showcase Repository

This `_showcase/` directory is configured as a standalone Git repository connected to:

**https://github.com/Kashan-A1i/Ishlogh-Architecture.git**

It is listed in the parent repository's `.gitignore` so that your private application repo and this public showcase repo remain completely separate.

---

## Initial Setup (If Initializing From Scratch)

```bash
cd _showcase
git init -b main
git add .
git commit -m "docs: initial Ishlogh architecture showcase"
git remote add origin git@github.com:Kashan-A1i/Ishlogh-Architecture.git
git push -u origin main
```

---

## Pushing Updates (Screenshots, Text Edits, Live URL)

Whenever you add screenshots to `_showcase/assets/` or update `README.md`:

```bash
cd _showcase
git status
git add .
git commit -m "docs: update showcase documentation and visuals"
git push origin main
```

---

## Pre-Push Privacy Check

Run this check from the root `Ishlogh` directory to verify no secrets or source code files were accidentally placed inside `_showcase/`:

```powershell
Get-ChildItem -Recurse -File _showcase -Exclude SETUP_PUBLIC_REPO.md |
  Select-String -Pattern 'SECRET_KEY\s*=|django-insecure|B2_APPLICATION_KEY\s*=|postgres://|AKIA|BEGIN .*PRIVATE KEY'
```

*(Expected output: empty)*
