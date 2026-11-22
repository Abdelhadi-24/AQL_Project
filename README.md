# AQL Project – Smart Rice Cooker Software

Embedded software for a smart rice cooker, developed by the **Road Runner** team for the client **FFE (Food For Everyone)**.
The project follows the **ISO/CEI TR 29110-5-1-2** guide (Basic profile for Very Small Entities), which has two processes:
**PM** (Project Management) and **SI** (Software Implementation).


## Team

| Role | Member |
|---|---|
| Gestionnaire de projet (PM) | Zidane Anaïs Melissa |
| Chef technique (TL) | Kaddour Abdelhadi Said |
| Analyste (AN) | Meberbeche Sarah |
| Concepteur (DES) | Bouzourine Achraf Rayan |
| Programmeur (PR) | Issad Abdelmalek |
| Équipe de travail (WT) | Reguieg Selma |

## Repository structure

```
AQL_Project/
├── README.md                          # project overview, team, how to navigate the repo, how to use GitHub
│
├── Client/
│   └── enonce-des-travaux/            # Énoncé des travaux v2.0 + cooking curves (input from FFE)
│
├── Gestion-de-projet/              # PM process (Tableau 10 of the guide)
│   ├── plan-de-projet/				# includes Directives de livraison + Stratégie de contrôle des versions
│   ├── specification-des-exigences/                
│   ├── demandes-de-changement/
│   ├── enregistrements-de-reunion/    # team and client meetings
│   ├── registre-des-corrections/
│   ├── enregistrements-d-avancement/  # weekly progress reports
│   ├── resultats-de-verification/     # verification of the Plan de projet
│   └── enregistrement-de-reception/   # signed acceptance record (closure)
│
├── Mise-en-oeuvre/                 # SI process: documents (Tableau 21 of the guide)
│   ├── specification-des-exigences/
│   ├── conception-du-logiciel/
│   ├── enregistrement-de-tracabilite/
│   ├── cas-et-procedures-de-test/     # test cases as documents
│   ├── rapport-de-test/
│   ├── documentation-utilisateur/
│   ├── guide-d-operation/
│   ├── documentation-maintenance/
│   ├── resultats-de-verification/     # SRS, design, test cases, docs reviews
│   └── resultats-de-validation/       # client validation of the SRS
│
├── Src/                               # Composants logiciels
└── Tests/
    ├── unitaires/
    └── integration/                   # executable tests (the Logiciel's tests)
```

### Where do I put my file?

- A **management** document (plan, meeting notes, progress report, change request...) goes in `Gestion-de-projet/`.
- A **software** document (requirements, design, test cases, manuals...) goes in `Mise-en-oeuvre/`.
- **Code** goes in `Src/`, **executable tests** in `Tests/`.
- Anything received from the client goes in `Client/`.

> This structure is a first version. It will be updated as the project moves forward.

---

# Git & GitHub Quick Guide

## Setup (once)

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git clone https://github.com/Abdelhadi-24/AQL_Project.git
cd AQL_Project
```

## Option A: Push straight to main

```bash
git pull  origin main                    # get the latest changes FIRST (main)
# ... edit your files ...
git status                    # see what changed
git add .                     # stage all changes
git commit -m "describe what you did"
git push origin main                     # send to GitHub (main)
```

## Option B: Work on your own branch, then merge

### 1. Create your branch

```bash
git switch main
git pull                           # start from the latest main
git switch -c my-branch-name       # create + switch to your branch
```

### 2. Work and push your branch

```bash
# ... edit your files ...
git add .
git commit -m "describe what you did"
git push -u origin my-branch-name  # first push of this branch
git push                           # later pushes
```

### 3. Merge your branch into main

```bash
git switch main
git pull                           # make sure main is up to date
git merge my-branch-name
git push
```

### 4. Clean up after merging

```bash
git branch -d my-branch-name              # delete the local branch
git push origin --delete my-branch-name   # delete it on GitHub (optional)
```

### Keep your branch up to date with main

```bash
git switch my-branch-name
git merge main
```

## Handy commands

| Command | What it does |
|---|---|
| `git status` | Show changed files |
| `git log --oneline` | Short commit history |
| `git diff` | Show what you changed |
| `git pull` | Download + merge latest changes |
| `git branch` | List local branches |
| `git switch branch-name` | Switch to a branch |
| `git restore file.py` | Discard your changes in a file |
| `git stash` / `git stash pop` | Shelve / restore uncommitted work |

## If `git push` is rejected

Someone pushed before you. Run:

```bash
git pull
git push
```

## If there's a merge conflict

1. Open the conflicted file and look for:
   ```
   <<<<<<< HEAD
   your version
   =======
   their version
   >>>>>>> main
   ```
2. Keep the correct code, delete the markers.
3. Then:
   ```bash
   git add .
   git commit -m "resolve conflict"
   git push
   ```

## Tips

- Always `git pull` before you start working.
- Commit small and often, with clear messages.