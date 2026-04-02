# Steel AF — Static Blog (steelafse.com)

A fast, free-to-host blog about steel built with [Hugo](https://gohugo.io/) and designed for deployment on Cloudflare Pages or Netlify. Live at [steelafse.com](https://steelafse.com).

---

## Quick Start

### 1. Install Hugo

**Mac:**
```bash
brew install hugo
```

**Windows:**
```bash
choco install hugo-extended
```

**Or download directly:** https://gohugo.io/installation/

### 2. Clone this repo and run locally

```bash
cd steel-blog
hugo server -D
```

Open `http://localhost:1313` in your browser. The site auto-reloads when you edit files.

### 3. Write a new post

```bash
hugo new posts/my-new-post.md
```

This creates a new Markdown file in `content/posts/` using the archetype template. Open it, write your content, and save — the local server will reflect changes instantly.

---

## Deploy to Cloudflare Pages (Recommended)

### Step 1: Push to GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/steelafse.git
git branch -M main
git push -u origin main
```

### Step 2: Connect to Cloudflare Pages

1. Go to [Cloudflare Dashboard](https://dash.cloudflare.com/) → **Workers & Pages** → **Create**
2. Select **Connect to Git** → authorize GitHub → select your `steel-blog` repo
3. Configure the build:
   - **Framework preset:** Hugo
   - **Build command:** `hugo --minify`
   - **Build output directory:** `public`
   - **Environment variable:** `HUGO_VERSION` = `0.145.0`
4. Click **Save and Deploy**

### Step 3: Connect your Namecheap domain

**In Cloudflare Pages:**
1. Go to your project → **Custom domains** → **Set up a custom domain**
2. Enter your domain: `steelafse.com`
3. Cloudflare will provide two nameservers

**In Namecheap:**
1. Log in → **Domain List** → click **Manage** next to your domain
2. Under **Nameservers**, select **Custom DNS**
3. Enter the two Cloudflare nameservers
4. Save changes (propagation takes a few minutes to 24 hours)

Cloudflare will automatically provision a free SSL certificate.

---

## Deploy to Netlify (Alternative)

1. Push to GitHub (same steps as above)
2. Go to [Netlify](https://app.netlify.com/) → **Add new site** → **Import an existing project**
3. Connect your GitHub repo
4. Build settings should auto-detect from `netlify.toml`
5. Click **Deploy**
6. Add your custom domain under **Domain management**
7. In Namecheap, point your domain's DNS to Netlify's nameservers or add a CNAME record

---

## Project Structure

```
steel-blog/
├── archetypes/         # Templates for new content
│   └── default.md
├── content/
│   ├── about.md        # About page
│   └── posts/          # Blog posts go here
├── layouts/
│   ├── _default/       # Page templates
│   ├── partials/       # Reusable components (header, footer)
│   └── index.html      # Homepage template
├── static/
│   ├── css/            # Stylesheet
│   └── images/         # Put images here
├── hugo.toml           # Site configuration
├── netlify.toml        # Netlify build config
└── wrangler.toml       # Cloudflare build config
```

## Writing Posts

Posts are Markdown files in `content/posts/`. Each post has front matter at the top:

```markdown
---
title: "Your Post Title"
date: 2026-04-01
draft: false
description: "A one-line summary for SEO and social sharing."
categories: ["Steel Grades"]
tags: ["4140", "alloy steel"]
---

Your content here. Use standard Markdown.
```

### Available categories (suggested starting set)
- Steel Grades
- Manufacturing
- Material Science
- Industry
- Guides

### Publishing workflow

1. Write your post in `content/posts/`
2. Preview locally: `hugo server -D`
3. Commit and push:
   ```bash
   git add .
   git commit -m "New post: title here"
   git push
   ```
4. Cloudflare/Netlify auto-builds and deploys (usually under 30 seconds)

---

## Customization

- **Site title, tagline, author:** Edit `hugo.toml`
- **Colors, fonts, layout:** Edit `static/css/style.css`
- **Navigation links:** Edit `[menu]` section in `hugo.toml`
- **Page templates:** Edit files in `layouts/`

---

## Cost

**$0/month.** Hugo is free. Cloudflare Pages and Netlify free tiers have no bandwidth limits worth worrying about for a blog. Your only cost is the domain renewal through Namecheap.
