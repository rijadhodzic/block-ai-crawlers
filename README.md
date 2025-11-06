# 🧱 Block AI Crawlers & Scrapers

A simple, open-source guide and configuration set to **block AI bots, scrapers, and search engines** from indexing or using your website content for training datasets.

---

## ⚡ Why this exists

In recent years, major AI companies have started crawling and copying website data to train their models without explicit permission.  
This repository provides simple configuration files to **protect your site from AI bots** like:
- GPTBot (OpenAI)
- ChatGPT-User
- Google-Extended
- CCBot (Common Crawl)
- ClaudeBot / Anthropic-AI
- PerplexityBot
- Amazonbot
- Applebot
- Others...

---

## 📁 Contents

| File | Description |
|------|--------------|
| `robots.txt` | Standard crawler rules (basic protection) |
| `.htaccess` | Apache configuration to fully block AI crawlers |
| `nginx.conf` | Nginx equivalent rule |
| `LICENSE` | MIT License |

---

## 🧩 1. Block via robots.txt

Create a file named `robots.txt` in your website root (`https://yourdomain.com/robots.txt`) and paste:

```txt
User-agent: *
Disallow: /

User-agent: GPTBot
Disallow: /

User-agent: ChatGPT-User
Disallow: /

User-agent: Google-Extended
Disallow: /

User-agent: CCBot
Disallow: /

User-agent: anthropic-ai
Disallow: /

User-agent: ClaudeBot
Disallow: /

User-agent: OAI-SearchBot
Disallow: /

User-agent: PerplexityBot
Disallow: /

User-agent: Amazonbot
Disallow: /

User-agent: Applebot
Disallow: /
```txt

## 🧱 2. Block via `.htaccess` (Apache)
If you’re using Apache, add this code to your `.htaccess` file in the web root:

```txt
<IfModule mod_rewrite.c>
RewriteEngine On

# Block AI bots and scrapers
RewriteCond %{HTTP_USER_AGENT} (GPTBot|ChatGPT|Google-Extended|CCBot|anthropic-ai|ClaudeBot|OAI-SearchBot|PerplexityBot|Amazonbot|Applebot) [NC]
RewriteRule .* - [F,L]
</IfModule>
```txt
