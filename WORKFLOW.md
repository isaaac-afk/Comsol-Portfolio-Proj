# Workflow: Adding a New COMSOL Project

A quick checklist to follow every time you finish a project. Keep it consistent and the portfolio builds itself.

## Each time you add a project

1. **Create the folder** with a number and short name:
   `02-microfluidic-mixer/` (use the next number, lowercase, dashes instead of spaces)

2. **Copy your COMSOL file** into it. Rename it to something descriptive:
   `model.mph` → `microfluidic-mixer.mph`

3. **Make an `images/` folder** inside and drop in 2–4 screenshots:
   - the geometry
   - the mesh
   - the main result plot

4. **Copy `TEMPLATE_inquiry.md`** into the folder, rename it to `README.md`, and fill it in.

5. **Add a row** to the projects table in the top-level `README.md`.

6. **Commit and push** (see below).

---

## Git commands (run from inside the repo folder)

First time only — connect the folder to GitHub:
```bash
git init
git add .
git commit -m "Initial commit: portfolio scaffold"
git branch -M main
git remote add origin https://github.com/isaaac-afk/comsol-portfolio.git
git push -u origin main
```

Every time after that:
```bash
git add .
git commit -m "Add project 02: microfluidic mixer"
git push
```

---

## Notes

- **File size:** GitHub blocks any single file over 100 MB. Most student `.mph` files are a few MB, so you're fine. If one is ever very large (>50 MB), tell me and I'll set up Git LFS.
- **`.mph` files are binary**, so GitHub can't show line-by-line changes — that's expected and fine for a portfolio.
- **Commit messages:** keep them short and descriptive ("Add project 03: heat sink fin study"). Future-you will thank present-you.
