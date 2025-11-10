---
layout: post
title: "I Built a Modern Jekyll Theme with Tailwind CSS (Free Template)"
date: 2025-11-10 11:50:00 +0330
tags: [jekyll, github, tailwindcss,webdev]
excerpt: "I recently needed a personal blog. I wanted something minimal, fast, and easy to customize. Most Jekyll themes felt outdated or overly complex, so I built my own."
toc: true
---

I recently needed a personal blog. I wanted something minimal, fast, and easy to customize. Most Jekyll themes felt outdated or overly complex, so I built my own.

## Meet al-minimal

A modern Jekyll theme powered by Tailwind CSS, designed specifically for developers who want to focus on writing, not theme configuration.

### Why Another Jekyll Theme?

**Problem 1: Outdated Design**
Most Jekyll themes look like they're from 2015. I wanted something that feels modern with a clean dark theme.

**Problem 2: Configuration Hell**
Many themes require hours of tweaking. I wanted something that works out of the box.

**Problem 3: GitHub Pages Compatibility**
Lots of themes don't deploy smoothly on GitHub Pages. This one does, with GitHub Actions handling everything automatically.

## Features

### 🎨 Modern Design
- Clean, minimal interface
- Beautiful dark theme
- Mobile-first responsive design
- Built with Tailwind CSS (utility-first approach)

### 📝 Content Focused
- Markdown blog posts
- Pagination (10 posts per page)
- Auto-generated table of contents
- Tags system for organization
- Projects portfolio section

### 🚀 Developer Experience
- One-click setup with GitHub template
- Automated GitHub Actions deployment
- Clean URLs (no `.html` extensions)
- Fast and lightweight
- Comprehensive documentation

### 🔍 SEO & Sharing
- Automatic sitemap generation
- Meta tags for social sharing
- RSS feed
- Twitter, LinkedIn, Facebook, Reddit, Telegram sharing

## Quick Start

### 1. Use the Template
Click "Use this template" on the [GitHub repo](https://github.com/alihtt/al-minimal) and name it `yourusername.github.io`

### 2. Configure
Edit `_config.yml`:
```yaml
title: Your Name
email: your-email@example.com
url: "https://yourusername.github.io"
icon: ⚛️

social:
  - icon: fa-brands fa-github
    link: https://github.com/yourusername
    name: GitHub
```

### 3. Add Content
Create `_posts/2025-01-15-my-first-post.markdown`:
```markdown
---
layout: post
title: "My First Post"
date: 2025-01-15 10:00:00 +0000
tags: [tutorial, getting-started]
excerpt: "A brief description"
---

Your content here...
```

### 4. Deploy
Push to GitHub. Actions deploys automatically to `https://yourusername.github.io`

That's it! 🎉

## Technical Decisions

### Why Tailwind CSS?
- **Utility-first:** No writing custom CSS
- **Consistent:** Design tokens built-in
- **Flexible:** Easy to customize
- **Modern:** Keeps the theme contemporary

### Why Jekyll?
- **GitHub Pages native support**
- **No server required**
- **Simple and reliable**
- **Markdown-based**

### Project Structure
```
.
├── _includes/      # Reusable components
├── _layouts/       # Page templates
├── _posts/         # Blog posts
├── _projects/      # Portfolio projects
├── assets/         # CSS, images
├── docs/           # Documentation
└── _config.yml     # Configuration
```

## Documentation
I wrote comprehensive guides:
- [Installation](https://github.com/alihtt/al-minimal/blob/master/docs/INSTALL.md)
- [Customization](https://github.com/alihtt/al-minimal/blob/master/docs/CUSTOMIZING.md)
- [Adding Content](https://github.com/alihtt/al-minimal/blob/master/docs/CONTENT.md)
- [Features Guide](https://github.com/alihtt/al-minimal/blob/master/docs/FEATURES.md)
- [Deployment](https://github.com/alihtt/al-minimal/blob/master/docs/DEPLOYMENT.md)
- [FAQ](https://github.com/alihtt/al-minimal/blob/master/docs/FAQ.md)

## What's Next?

Considering adding:
- Dark/light theme toggle
- Search functionality
- Series/multi-part posts
- Reading time estimates

What features would you want? Drop a comment!

## Try It Out

🔗 **GitHub:**  [https://github.com/alihtt/al-minimal](https://github.com/alihtt/al-minimal)
📄 **License:** MIT (use it however you want!)
⭐ **Star it** if you find it useful!
