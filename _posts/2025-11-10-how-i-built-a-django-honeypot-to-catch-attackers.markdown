---
layout: post
title: "How I Built a Django Honeypot to Catch Attackers (and What I Learned)"
date: 2025-11-10 11:43:00 +0330
tags: [django, python, opensource,security]
excerpt: "If you've ever run a Django site, you've probably seen the endless stream of bots trying to brute-force your `/admin/` page. After watching my logs fill up with failed login attempts, I decided to do something about it."
toc:
  - id: the-problem
    title: The Problem
  - id: the-solution-honeyguard
    title: "The Solution: HoneyGuard"
    subsections:
      - id: 1-fake-login-pages
        title: Fake Login Pages
      - id: 2-behavioral-detection
        title: Behavioral Detection
      - id: 3-intelligence-gathering
        title: Intelligence Gathering
      - id: 4-alerts--integration
        title: Alerts & Integration
  - id: quick-start
    title: Quick Start
  - id: what-i-learned
    title: What I Learned
  - id: try-it-out
    title: Try It Out
  - id: whats-next
    title: What's Next
---

If you've ever run a Django site, you've probably seen the endless stream of bots trying to brute-force your `/admin/` page. After watching my logs fill up with failed login attempts, I decided to do something about it.

## The Problem

Attackers know Django uses `/admin/` by default. They hammer it with credential stuffing, brute force attacks, and automated scanners. While rate limiting helps, it's reactive. I wanted something proactive.

## The Solution: HoneyGuard

I built **HoneyGuard**, a Django package that creates fake admin login pages (honeypots). Here's how it works:

### 1. Fake Login Pages
Move your real admin to `/secret-admin/` (or whatever), and let HoneyGuard serve a convincing fake at `/admin/`. Attackers waste their time, and you gather intel.

### 2. Behavioral Detection
HoneyGuard catches:
- **Too-fast submissions** (< 2 seconds = bot)
- **Too-slow submissions** (> 10 minutes = abandoned form or scanner)
- **Hidden honeypot fields** (invisible fields that bots fill out)

### 3. Intelligence Gathering
Every attempt is logged with:
- IP address, user agent, timestamp
- Username/password length (not the actual password!)
- Risk score based on detected anomalies
- Request timing and suspicious patterns

### 4. Alerts & Integration
- Email alerts for high-risk attempts
- Django signals for custom handlers
- Console logging for development

## Quick Start
```bash
pip install django-honeyguard
```
```python
# settings.py
INSTALLED_APPS = [
    'django_honeyguard',
]

HONEYGUARD = {
    'EMAIL_RECIPIENTS': ['security@example.com'],
    'ENABLE_CONSOLE_LOGGING': True,
}
```
```python
# urls.py
urlpatterns = [
    path('', include('django_honeyguard.urls')),
    path('secret-admin/', admin.site.urls),  # Your real admin
]
```

That's it! Now `/admin/` is a honeypot, and your real admin is safely hidden.

## What I Learned

**1. Timing attacks are real:** Bots submit forms in milliseconds. Humans take 5-30 seconds minimum.

**2. WordPress wannabes:** You'd be surprised how many bots hit `/wp-admin.php` on Django sites. HoneyGuard includes a fake WordPress login too.

**3. Fail fast validation:** I validate all settings at Django startup, so you catch config errors immediately.

**4. Signals > callbacks:** Using Django's signal system makes it easy for users to integrate custom behavior without modifying HoneyGuard.

## Try It Out

- 📦 **PyPI:** `pip install django-honeyguard`
- 📚 **Docs:** [https://django-honeyguard.readthedocs.io](https://django-honeyguard.readthedocs.io)
- 🔗 **GitHub:** [https://github.com/alihtt/django-honeyguard](https://github.com/alihtt/django-honeyguard)

## What's Next?

I'm considering adding:
- Geo-IP blocking for repeat offenders
- Machine learning for pattern detection
- Integration with fail2ban

What features would you find useful? Drop a comment!
