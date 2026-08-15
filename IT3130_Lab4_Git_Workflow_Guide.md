# IT3130 — Lab Sheet 4: Version Controlling with Git II
### Branching, Pull Requests, Peer Review & GitHub Flow — Working Checklist

> **How to use this file:** Work through the checkboxes top to bottom in your IDE.
> Where a command block is given, ask your agent to run it in the terminal inside your
> cloned repo folder. Replace all `<placeholders>` first (see below). Steps involving
> the GitHub *website* (creating repo, opening/merging PRs, inviting a collaborator)
> must be done by you in the browser — an agent can't click buttons on github.com,
> but it can prep the files/commits and give you the exact next click.

---

## 0. Fill in your placeholders

Before starting, decide these values and swap them in everywhere below:

| Placeholder | Your value |
|---|---|
| `<student-id>` | e.g. `it21xxxxxx` |
| `<repository-url>` | the HTTPS/SSH clone URL of your new GitHub repo |
| `<repository-folder>` | local folder name after cloning |
| `<short-feature-name>` | e.g. `profile-page` |
| `<colleague-username>` | your pair partner's GitHub username |

Branch naming convention (fixed by the lab): `feature/<student-id>/<short-feature-name>`

---

## Part 1 — Individual Work

- [ ] **1. Create a new public GitHub repository** on github.com (add a README if you like).
- [ ] **2. Clone it locally and open a terminal in it.**
  ```bash
  git clone <repository-url>
  cd <repository-folder>
  ```
- [ ] **3. Confirm git identity is configured** (prerequisite check):
  ```bash
  git config --global user.name
  git config --global user.email
  ```
- [ ] **4. Create and switch to a feature branch:**
  ```bash
  git switch -c feature/<student-id>/profile-page
  ```
- [ ] **5. Add one or more small files** (text/HTML/source) with an easily identifiable change — e.g. a simple `profile.html`.
- [ ] **6. Inspect, stage, commit, and push:**
  ```bash
  git status
  git add .
  git commit -m "Add profile page structure"
  git push -u origin feature/<student-id>/profile-page
  ```
- [ ] **7. On GitHub:** verify the branch and files appear.
- [ ] **8. On GitHub:** open a pull request with `main` as the base branch. Write a concise title and describe *what changed* and *how you checked it*.
- [ ] **9. On GitHub:** review the changed files yourself, then **merge** the PR and **delete** the remote feature branch.
- [ ] **10. Sync local main and confirm clean tree:**
  ```bash
  git switch main
  git pull origin main
  git status
  ```

**Evidence to save now:** repo URL, feature branch name + screenshot, merged PR URL.

---

## Part 2 — Pair Collaboration

> Rule: never share passwords/tokens/credentials — collaborate only via GitHub invites, branches, and PRs.

Decide who is **Student A** (repo owner) and **Student B** (contributor) for round 1, then swap for round 2.

- [ ] **1.** Student A → GitHub repo Settings → Collaborators → invite `<colleague-username>`.
- [ ] **2.** Student B accepts the invite, then clones A's repo into a **separate** local folder:
  ```bash
  git clone <A-repository-url>
  cd <A-repository-folder>
  ```
- [ ] **3.** Student B creates a feature branch, makes a small change, commits:
  ```bash
  git switch -c feature/<student-B-id>/<short-feature-name>
  # edit a file
  git add .
  git commit -m "Describe the small change"
  ```
- [ ] **4.** Student B pushes and opens a PR into A's `main`:
  ```bash
  git push -u origin feature/<student-B-id>/<short-feature-name>
  ```
- [ ] **5.** Student A reviews the PR on GitHub, leaves at least one review comment or an approval.
- [ ] **6.** *(If changes requested)* Student B commits more changes on the **same branch** and pushes again — the PR updates automatically:
  ```bash
  git add .
  git commit -m "Address review feedback"
  git push
  ```
- [ ] **7.** Student A merges the PR and deletes the remote feature branch.
- [ ] **8.** **Reverse roles** — repeat steps 1–7 with B as owner and A as contributor.

**Evidence to save now:** URL of the PR you contributed to / reviewed in your colleague's repo.

---

## Part 3 — GitHub Flow (full cycle, solo run-through)

- [ ] **1. Update local main before starting new work:**
  ```bash
  git switch main
  git pull origin main
  ```
- [ ] **2. Branch, commit, push** (repeat Part 1 steps 4–6 with a new feature name if you want a fresh cycle).
- [ ] **3. Open PR → ask for review → respond to feedback on the same branch → test.**
- [ ] **4. After approval, merge and delete the feature branch on GitHub.**
- [ ] **5. Clean up locally:**
  ```bash
  git switch main
  git pull origin main
  git branch -d feature/<student-id>/<short-feature-name>
  git fetch --prune
  ```
- [ ] **6. Capture the commit graph for your evidence:**
  ```bash
  git log --oneline --graph --decorate --all
  ```
  Save this output to a file for your submission, e.g.:
  ```bash
  git log --oneline --graph --decorate --all > commit-history.txt
  ```

---

## Part 4 — Submission Package

### A. Evidence checklist (5 marks) — gather these

- [ ] Repository URL (public GitHub repo)
- [ ] Feature branch name + screenshot of it on GitHub
- [ ] URL of the merged pull request + reviewer's GitHub username
- [ ] Output/screenshot of `git log --oneline --graph --decorate --all`
- [ ] URL of the pull request you contributed to or reviewed in your colleague's repo

### B. Written questions (20 marks) — answer in your own words

These are assessed against a submission declaration that the work is your own,
so answer them yourself rather than having an agent generate them. Use the
prompts below as your answer template.

1. **[2 marks]** Difference between `git branch <name>` and `git switch -c <name>`:
   >
2. **[3 marks]** Why develop a new feature in a feature branch instead of directly in `main`?
   >
3. **[2 marks]** What does `git push -u origin <branch-name>` achieve?
   >
4. **[3 marks]** Purpose of a pull request, and what a reviewer should check before approving:
   >
5. **[4 marks]** Describe the GitHub Flow sequence from starting a feature to completing the work:
   >
6. **[2 marks]** Why are meaningful branch names and small atomic commits important in team development?
   >
7. **[2 marks]** Why is it good practice to delete a feature branch after it's merged?
   >
8. **[2 marks]** Steps to safely resolve a PR conflict with `main` and update the PR:
   >

### Final step

- [ ] Combine the evidence (screenshots/links) + your answers into **one PDF** and submit, with the submission declaration included.

---

*Source: IT3130 Application Development — Lab Sheet 4, Year 3 Semester 1 2026, Faculty of Computing.*
