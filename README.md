# Dries De Ridder — Portfolio Site

Personal portfolio site. Static HTML + CSS, no build step, no framework.
Made to be deployed on GitHub Pages with a custom domain.

## File structure

```
/
├── index.html       Home page
├── projects.html    Case studies
├── styles.css       All styles (shared)
├── resume.pdf       Your CV (you need to add this)
└── images/          Screenshots, portrait, project art
    ├── portrait.jpg
    ├── blackwood.jpg
    ├── spectr.jpg
    └── ... etc
```

## Before you deploy — quick customisation checklist

Open `index.html` and `projects.html` in any text editor and update:

1. **Email** — Search-and-replace `hello@driesderidder.dev` with your real email.
2. **Social links** — Replace the three `https://linkedin.com/`, `https://github.com/`,
   `https://medium.com/` placeholders with your actual profile URLs (search the files
   for each).
3. **Article links** — In `index.html`, the two Medium article links point to
   `https://medium.com/`. Replace with the real article URLs.
4. **Stats** — In `index.html` under `<!-- STATS -->`, edit the numbers (6+ years,
   5 titles, etc.) to whatever's accurate today.
5. **Resume** — Drop your CV into the repo root as `resume.pdf`. The "Download CV"
   button already points to it.
6. **Portrait** — Drop a photo into `/images/portrait.jpg`. The hero will pick it up
   automatically; until then, a placeholder shows.
7. **Project images** — When you have screenshots, replace the gradient placeholders.
   The simplest way: in `styles.css` find `.project-img.blackwood` (and the other
   project classes) and swap the `background:` line for:
   ```css
   .project-img.blackwood {
     background: url('images/blackwood.jpg') center/cover no-repeat;
   }
   ```
   Then remove or hide the `[ ... ]` placeholder div in the HTML.
8. **Copy** — Read both files top to bottom and tweak anything that doesn't sound
   like you. Especially the hero headline and About paragraphs.

## Deploy to GitHub Pages

### One-time setup

1. Create a public GitHub repo named **exactly** `<your-username>.github.io`
   (e.g. `driesderidder.github.io`). The name matters — that pattern makes
   GitHub Pages auto-serve it at the root domain.
2. Push these files to the `main` branch. Easiest path if you don't want to use
   the command line: open the new repo on GitHub, click **Add file → Upload files**,
   drag everything in, commit.
3. Go to **Settings → Pages**. Under "Source", choose **Deploy from a branch**,
   pick `main` / `(root)`, save.
4. Wait ~30 seconds. The site is live at `https://<your-username>.github.io`.

### Custom domain

1. Buy your domain. Cloudflare Registrar is the cheapest with no markup; Porkbun
   and Namecheap are also fine. `driesderidder.dev` would be a clean choice.
2. In your registrar's DNS settings, add these records:
   ```
   A     @     185.199.108.153
   A     @     185.199.109.153
   A     @     185.199.110.153
   A     @     185.199.111.153
   CNAME www   <your-username>.github.io
   ```
3. Back in **GitHub → Settings → Pages → Custom domain**, type your domain
   (e.g. `driesderidder.dev`), save.
4. Once GitHub confirms DNS, tick **Enforce HTTPS**. Done.

DNS can take an hour to propagate, sometimes less.

## Updating the site later

Edit any file, commit, push. Live in ~30 seconds.

If you prefer the web flow: open the file on github.com, click the pencil icon,
edit, commit. Same result.

## Browser support

Modern Chrome, Firefox, Safari, Edge. Uses CSS Grid, custom properties, and
`backdrop-filter`. No JavaScript anywhere.

## Why no framework?

This site loads in under 50ms because it's two HTML files and one CSS file.
You can read every line of it. When you want to change something, you change
exactly that thing — no build, no bundler, no `node_modules`. If you eventually
want a CMS for blog posts or per-project pages, the right next step is Astro,
not Next.js.

— Built May 2026
