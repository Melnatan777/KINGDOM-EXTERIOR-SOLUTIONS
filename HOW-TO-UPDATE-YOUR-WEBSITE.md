# How to Update Your Website
### Kingdom Exterior Solutions — Simple Guide

---

## The Big Picture

Your website lives in 3 places that work together:

1. **This folder on your computer** — where the actual files are
2. **GitHub** — an online backup that stores every version of your site
3. **Cloudflare** — watches GitHub and publishes your site live automatically

When Claude makes a change to a file in this folder, it's updated on your computer instantly. You then push it to GitHub, and Cloudflare picks it up and goes live in about 30 seconds.

---

## Your Workflow (Every Time)

### Step 1 — Ask Claude to make changes
Just tell Claude what you want in plain English. Examples:
- *"Update the services page with these 4 services..."*
- *"Change the phone number on every page"*
- *"Add a new testimonial from James in Houston"*

Claude writes directly into the files in this folder. You don't touch any code.

---

### Step 2 — Open GitHub Desktop

Open the **GitHub Desktop** app on your computer.

You'll see a screen that looks like this:

```
Changes  |  History

  contact.html        (modified)
  about.html          (modified)
```

Any file Claude changed will show up here automatically.

---

### Step 3 — Commit the changes

At the bottom left of GitHub Desktop you'll see a box that says:

> **Summary (required)**

Type a short note about what changed. Examples:
- *Updated services page*
- *Fixed phone number*
- *Added new testimonial*

Then click the blue **"Commit to main"** button.

---

### Step 4 — Push to GitHub

After committing, you'll see a button at the top that says:

> **Push origin**

Click it. This sends your changes up to GitHub.

---

### Step 5 — Wait 30 seconds

Cloudflare sees the new files on GitHub and automatically rebuilds your live website. That's it — your site is updated.

You can check it at:
👉 https://kingdom-exterior-solutions.pages.dev

---

## Quick Reference Card

| What you want | What you do |
|---|---|
| Change text or add content | Ask Claude |
| See what changed | Open GitHub Desktop |
| Save the change | Click **Commit to main** |
| Make it go live | Click **Push origin** |
| Check the live site | Visit your pages.dev link |

---

## Things to Know

- **Claude can't push to GitHub for you** — that one click is yours to do
- **You can always undo** — GitHub saves every version, nothing is permanent
- **If something looks wrong on the live site**, just ask Claude to fix it and push again
- **Don't edit files yourself** unless you're comfortable with code — let Claude handle it

---

## Your Important Links

- **Live site:** https://kingdom-exterior-solutions.pages.dev
- **GitHub repo:** https://github.com/Melnatan777/KINGDOM-EXTERIOR-SOLUTIONS
- **Cloudflare dashboard:** https://dash.cloudflare.com

---

*Saved in your project folder so you can find it anytime.*
