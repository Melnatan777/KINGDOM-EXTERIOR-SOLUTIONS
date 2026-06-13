# How Claude Updates Your Website
### The Full Picture — With Code Examples

---

## The 5-Part System

```
YOUR COMPUTER (folder)
      ↓
   Claude writes files directly here
      ↓
GITHUB DESKTOP
      ↓
   Claude commits + pushes
      ↓
GITHUB (online backup)
      ↓
   Cloudflare watches GitHub automatically
      ↓
CLOUDFLARE → YOUR LIVE WEBSITE
```

Every time Claude makes a change, this whole chain happens in under 2 minutes.

---

## Part 1 — The Folder Connection

When you clicked the folder icon in Cowork and selected your folder, Cowork gave Claude direct access to your files at this path on your computer:

```
C:\Users\mbill\Documents\GIT HUB\GIT HUB\KINGDOM-EXTERIOR-SOLUTIONS\
```

Claude can now **read, write, and edit** any file inside that folder — just like you would in Notepad or Word, except Claude does it instantly without you opening anything.

---

## Part 2 — How Claude Writes a File

When you asked Claude to build the gallery page, Claude used a **Write tool** behind the scenes. Think of it like this:

```
You say:   "Build me a Before & After gallery page"

Claude:    Opens gallery.html in your folder
           Writes 668 lines of HTML code
           Saves the file
           Done — file is updated on your computer instantly
```

The actual file Claude created looks like this at the top:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Before & After Gallery | Kingdom Exterior Solutions</title>
    <link rel="stylesheet" href="css/style.css">
    ...
```

And inside, each before/after project card is structured like this:

```html
<!-- PROJECT 1: Driveway -->
<!-- TO UPDATE: Replace gallery-1.webp (before) and gallery-2.webp (after) -->
<div class="project-card" data-category="pressure-washing">

    <div class="before-after-pair">

        <div class="before-block">
            <span class="before-label">Before</span>
            <img src="images/gallery-1.webp" alt="Driveway before">
        </div>

        <div class="after-block">
            <span class="after-label">After</span>
            <img src="images/gallery-2.webp" alt="Driveway after">
        </div>

    </div>

    <div class="project-info">
        <span class="project-tag">Pressure Washing</span>
        <h3>Driveway Restoration — Friendswood, TX</h3>
        <p>Years of oil stains wiped away in a single visit.</p>
    </div>

</div>
```

When Tanner gets real photos, Claude just swaps the image filenames — e.g. replacing `gallery-1.webp` with `tanners-job-june-driveway-before.webp`.

---

## Part 3 — How the Filter Buttons Work

The gallery page has buttons that let visitors filter by service type. This is powered by a small piece of JavaScript at the bottom of the file:

```javascript
function filterProjects(category, btn) {

    // Highlight the clicked button
    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');

    // Show or hide cards based on their category tag
    document.querySelectorAll('.project-card').forEach(card => {
        if (category === 'all') {
            card.style.display = '';           // show everything
        } else if (card.dataset.category === category) {
            card.style.display = '';           // show matching cards
        } else {
            card.style.display = 'none';       // hide non-matching cards
        }
    });

}
```

Each project card has a `data-category` tag that tells the filter what type it is:

```html
<div class="project-card" data-category="roof-cleaning">
```

When a visitor clicks "Roof Cleaning", the filter finds all cards with `data-category="roof-cleaning"` and shows only those.

---

## Part 4 — How Claude Pushed to GitHub

After writing the file, Claude opened GitHub Desktop on your computer using its **computer control tools** — it can see your screen and click buttons just like a person would.

Here's what Claude did, step by step:

```
1. Opened GitHub Desktop
2. Saw "2 changed files" listed:
      - gallery.html       (new page)
      - HOW-TO-UPDATE-YOUR-WEBSITE.md  (new guide)
3. Clicked the Summary box and typed:
      "Add gallery page and how-to guide"
4. Clicked "Commit 2 files to main"
5. Clicked "Push origin"
6. GitHub Desktop showed "Refreshing repository..."
7. Finished — "No local changes / Last fetched just now"
```

Under the hood, those clicks ran these git commands:

```bash
# Stage all changed files
git add gallery.html HOW-TO-UPDATE-YOUR-WEBSITE.md

# Save a snapshot with a description
git commit -m "Add gallery page and how-to guide"

# Send it up to GitHub
git push origin main
```

You don't need to understand git commands — Claude handles it. But now you know what's happening behind the scenes.

---

## Part 5 — How Cloudflare Takes Over

Once the push lands on GitHub, Cloudflare Pages detects the change automatically (it watches your repo 24/7) and rebuilds your live website. You don't touch Cloudflare at all.

```
GitHub gets the push
      ↓
Cloudflare detects new commit (within seconds)
      ↓
Cloudflare rebuilds the site (about 30 seconds)
      ↓
Your live site is updated at:
https://kingdom-exterior-solutions.pages.dev
```

---

## What Each File Does

Here's a plain-English map of your project folder:

```
KINGDOM-EXTERIOR-SOLUTIONS/
│
├── index.html          ← Homepage (hero, services, gallery preview, reviews, CTA)
├── about.html          ← About page (story, Christian values, promise)
├── contact.html        ← Contact page (form, phone, email, map)
├── gallery.html        ← Before & After gallery (filter by service type)
├── services.html       ← Services page (not built yet)
├── reviews.html        ← Reviews page (not built yet)
│
├── css/
│   └── style.css       ← All the colors, fonts, layout for every page
│
├── images/
│   └── *.webp          ← All photos used on the site
│
├── js/
│   └── main.js         ← Any JavaScript (currently empty)
│
└── HOW-TO-UPDATE-*.md  ← These guides (for reference)
```

---

## How to Add a Real Job Photo (When Tanner Gets One)

1. Tanner takes a Before photo and an After photo on his phone
2. Send them to your computer and save them in the `images/` folder
   - Name them something clear, like: `driveway-before-pearland-june.webp`
3. Tell Claude: *"Add a new driveway before/after from Pearland — the before photo is driveway-before-pearland-june.webp and the after is driveway-after-pearland-june.webp"*
4. Claude updates `gallery.html` with the new card
5. Claude opens GitHub Desktop, commits, and pushes
6. Live in 30 seconds

---

## Quick Glossary

| Word | What it means |
|---|---|
| **HTML** | The code that builds the structure of a webpage (headings, images, buttons) |
| **CSS** | The code that styles the page (colors, fonts, spacing) |
| **JavaScript** | Code that makes the page interactive (like the filter buttons) |
| **Git** | A system that tracks every change ever made to your files |
| **Commit** | Saving a snapshot of your changes with a description |
| **Push** | Sending your commits up to GitHub |
| **Deploy** | Cloudflare publishing your latest files to the live website |
| **Repository (repo)** | Your project folder tracked by Git — lives on your computer AND on GitHub |

---

*Saved in your project folder. Claude can update your site anytime — just ask.*
