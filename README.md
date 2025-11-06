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

## 📋 Contents

| File | Description |
|------|-------------|
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
```

---

## 🧱 2. Block via `.htaccess` (Apache)

If you're using Apache, add this code to your `.htaccess` file in the web root:

```apache
<IfModule mod_rewrite.c>
RewriteEngine On

# Block AI bots and scrapers
RewriteCond %{HTTP_USER_AGENT} (GPTBot|ChatGPT|Google-Extended|CCBot|anthropic-ai|ClaudeBot|OAI-SearchBot|PerplexityBot|Amazonbot|Applebot) [NC]
RewriteRule .* - [F,L]
</IfModule>
```

This returns `403 Forbidden` to blocked crawlers.

---

## ⚙️ 3. Block via Nginx

If you're running Nginx, edit your site config (`/etc/nginx/sites-available/example.com`):

```nginx
if ($http_user_agent ~* (GPTBot|ChatGPT|Google-Extended|CCBot|anthropic-ai|ClaudeBot|OAI-SearchBot|PerplexityBot|Amazonbot|Applebot)) {
    return 403;
}
```

Then reload:

```bash
sudo systemctl reload nginx
```

---

## 🔒 4. Add "no AI" headers & meta tags

For extra protection, add these in your HTML `<head>`:

```html
<meta name="robots" content="noindex, nofollow">
<meta name="googlebot" content="noai">
<meta name="bingbot" content="noai">
<meta name="anthropic-ai" content="noai">
<meta name="openai" content="noai">
<meta name="perplexity-ai" content="noai">
```

Or in your Apache config:

```apache
Header set X-Robots-Tag "noindex, noai, noimageai"
```

---

## 🛡️ 5. Optional: Advanced protection

For even stronger protection:

- Use **Cloudflare Firewall** to block known AI crawler IPs or patterns.
- Enable **rate limiting** to stop mass scrapers.
- Use **CAPTCHA** or JS challenges on high-value pages.
- Monitor access logs for unusual bot behavior.

---

## 🤝 Contributing

Feel free to open a Pull Request to add new AI bots or improvements.  
If you find a new crawler, please share its user-agent and source.

---

## 📄 License

MIT License - Feel free to use and modify as needed.
