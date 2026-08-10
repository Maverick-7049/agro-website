# Agro Website — Deploy Reference

**Project:** The Impact Engine / Agro — agri-communications marketing site
**Live URL target:** `https://agro.theimpactengine.in`
**Type:** Static multi-page site — no build step, no server, no database
**Deployed the same way as** `ai.theimpactengine.in` (Hostinger static hosting)

---

## 1. What This Is

A 4-page marketing website:

| Page | File |
|---|---|
| Home | `index.html` |
| About | `about.html` |
| Services | `services.html` |
| Contact | `contact.html` |

Shared stylesheet in `css/styles.css`, logos in `assets/`. All links are relative, so
the folder works unchanged at the root of any domain or subdomain.

Unlike `ai.theimpactengine.in`, this site needs **no Supabase, no edge function, no
database, no auth**. It is pure HTML/CSS. Nothing to configure before going live.

External resources loaded over CDN (work automatically on the live domain):
- Google Fonts — Bitter + Archivo
- Stock imagery — Unsplash
- Stock video — Pexels

---

## 2. Deploy to Hostinger (same flow as the AI platform)

1. Log in to **Hostinger control panel → Domains → Subdomains**
2. Create subdomain: `agro` → it maps to `public_html/agro.theimpactengine.in/`
3. Open **File Manager** (or connect by FTP) and go to
   `public_html/agro.theimpactengine.in/`
4. Upload the **contents** of this folder so the structure is:
   ```
   public_html/agro.theimpactengine.in/
   ├── index.html
   ├── about.html
   ├── services.html
   ├── contact.html
   ├── css/
   │   └── styles.css
   └── assets/
       ├── logo-black-transparent.png
       └── logo-white-transparent.png
   ```
   > Easiest path: upload `agro-website.zip`, then use File Manager's **Extract**
   > so the files land directly in the subdomain folder (not inside an extra
   > `agro-website/` subfolder).

That's it — the site is live at `https://agro.theimpactengine.in`.
Hostinger provisions HTTPS for the subdomain automatically (may take a few minutes).

---

## 3. Before / after launch — optional polish

- **Book a Call** buttons point to `https://calendly.com/theimpactengine`.
  Update that URL across the 4 files if the real Calendly handle differs.
- **Contact form** has no backend; on submit it opens the visitor's email client
  addressed to `agro@theimpactengine.in`. To capture submissions directly instead,
  wire the form to a form service (Formspree / Web3Forms) or a Supabase table.
- **Stock media** (Unsplash photos, Pexels video) is placeholder. Swap for
  licensed/owned agriculture footage and photography before a hard public launch.

---

## 4. Design System (locked)

| Token | Value |
|---|---|
| Background | `#f2f0ea` (warm cream) |
| Surface | `#e8e5db` |
| Foreground / Border | `#141412` (near-black) |
| **Accent** | `#b61010` (deep red) |
| Display font | Bitter (700 / 900), uppercase |
| Body font | Archivo (400–800) |
| Borders | 3px cards / 4px section dividers, no radius, no shadows |
| Max width | 1240px, page padding `clamp(20px, 5vw, 64px)` |

Industrial, high-contrast, flat. All tokens live as CSS variables at the top of
`css/styles.css` — change them there to retheme the whole site.
