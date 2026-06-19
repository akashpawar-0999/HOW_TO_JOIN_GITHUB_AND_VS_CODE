# Connecting a New Local Folder to a GitHub Repository

## The Problem
I use GitHub from VS Code. After I'm done coding, to upload to GitHub I do:
1. `git status`
2. `git add .`
3. `git commit -m "description"` → it gets added to my repo and gives a green contribution square on my profile.

Now I want to create a **new folder for MySQL learnings** and connect it to GitHub — just like I connected my other 2 folders.

---

## Full Process: Create a New Local Folder and Connect It to a New GitHub Repo

---

### Step 1 — Create the Folder on Your PC

Make a new folder anywhere on your PC, e.g. `MySQL-Practice`.

Open it in VS Code:
**File → Open Folder → select your new folder**

---

### Step 2 — Create a New Repo on GitHub

1. Go to [github.com](https://github.com) → click the **+** icon (top right) → **New repository**
2. Give it a name (e.g. `MySQL-Practice`)
3. Keep it **Public** (so contributions count ✅)
4. **Do NOT** check "Add a README" — keep it empty for now
5. Click **Create repository**

GitHub will show you a page with setup commands — keep it open.

---

### Step 3 — Initialize Git in Your Folder (VS Code Terminal)

Open the terminal in VS Code (`Ctrl + `` ` ```) and run these one by one:

```bash
git init
```

```bash
git remote add origin https://github.com/YOUR_USERNAME/MySQL-Practice.git
```

> Replace `YOUR_USERNAME` and `MySQL-Practice` with your actual GitHub username and repo name.

```bash
git branch -M main
```

---

### Step 4 — Add a First File and Push

Create any file inside the folder (e.g. `README.md`), then run:

```bash
git add .
git commit -m "initial commit"
git push -u origin main
```

The `-u origin main` part links your local folder to GitHub **permanently**.

After this first push, for all future uploads you just do your usual:

```bash
git status
git add .
git commit -m "your message"
git push
```

---

## Why `git push -u origin main` Only Once?

| Command | What it does |
|---|---|
| `git remote add origin <url>` | Tells Git *where* GitHub is |
| `git branch -M main` | Renames branch to `main` |
| `git push -u origin main` | Pushes + sets default upstream (only needed once) |
| `git push` (future) | Works directly after the above |

After this, every `git push` will show up as a **green contribution square** on your profile, just like your other repos. ✅

---

## Is This Done?

Yes, it's done! ✅

Your terminal output confirms everything worked perfectly:

- `1 file changed, 48 insertions(+)` → your README.md was pushed
- `create mode 100644 README.md` → file was created on GitHub
- `new branch: main → main` → branch is linked
- `branch 'main' set up to track 'origin/main'` → future `git push` will work directly

---

## Ongoing Workflow (Every Time After Setup)

```bash
git add .
git commit -m "your message"
git push
```

No need for `-u origin main` again. Go ahead and start adding your SQL files!

---

## Can I Use Only `git add .`?

**No**, `git add .` alone won't work. You need **all 3 commands** every time.

Here's why each one is necessary:

| Command | What it does | If you skip it |
|---|---|---|
| `git add .` | Stages your changes (marks files as "ready to upload") | Changes won't be included |
| `git commit -m "msg"` | Saves a snapshot of your changes locally | Nothing to push, push will fail |
| `git push` | Actually uploads to GitHub | Code stays on your PC only |

### Think of it like sending a courier package:

- `git add .` → **Pack the items** into the box
- `git commit` → **Seal the box** with a label
- `git push` → **Send the box** to GitHub

You can't send a box that isn't sealed, and you can't seal a box you haven't packed.

---

## Pro Tip: Run All 3 as One Single Line

```bash
git add . ; git commit -m "your message" ; git push
```

Paste that in the terminal and all 3 run back to back automatically. 🚀
