# Ahmadiyyat Path

A public, self-paced course following the New Ahmadi Tarbiyyat Syllabus: 8 modules, 128 lessons written in plain English, a checkpoint quiz at the end of each module that unlocks the next, and the ten conditions of bai'at. Visitors create a free account (name + password) and their progress follows them across phone and computer.

- `public/index.html` — the whole site
- `api/auth.js` — create account / sign in / sign out (passwords hashed with scrypt; 10 wrong attempts locks a name for 15 min; 10 new accounts per network per hour)
- `api/progress.js` — saves and loads the signed-in learner's progress
- Data: Upstash Redis via Vercel Storage. No npm packages, no build step.

## Deploy
1. Create a new GitHub repo and upload the contents of this folder (`api/`, `public/`, `README.md`) to the top level.
2. vercel.com → Add New → Project → import the repo. Framework preset: **Other**. Leave build settings empty. Deploy.
3. Project → **Storage → Create Database → Upstash (Redis)** → free plan → Connect to this project (all environments).
4. **Deployments → ⋯ → Redeploy.**
5. Open the site and create a test account. The badge on the home screen should read "Synced to your account".

## Changing the pass mark
Checkpoints require every answer correct. In `public/index.html`, change `const PASS=1` to `0.8` for 80%.
