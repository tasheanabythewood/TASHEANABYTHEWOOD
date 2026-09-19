# Publishing this site

Static HTML, no build step, no framework, no dependencies. Two repositories.

| Repository | Holds | Why separate |
| --- | --- | --- |
| `cincy-311-service-performance` | The analysis: Python, SQL, reports | A technical reviewer clones this and runs it |
| `<your-github-username>.github.io` | This site: all projects, about, contact | One site, one identity, free hosting |

The site links out to the analysis repo. Keeping them apart means a reviewer who
wants the code is not digging through HTML, and a recruiter who wants the story
is not looking at Python.

## 1. Fill in the placeholders

Search both HTML files for `[YOUR` and replace every match:

- `[YOUR NAME]` in the header, title and footer of both pages
- `[YOUR EMAIL]`, `[YOUR-LINKEDIN]`, `[YOUR-GITHUB]` in `index.html`
- `[YOUR-GITHUB]` in the GitHub link at the bottom of `cincinnati-311.html`
- `[YOUR-NAME]-resume.pdf` if you add a resume to `assets/`
- The About section in `index.html`

## 2. Copy the charts in

From the analysis project:

```
copy reports\charts\*.png site\assets\charts\
```

Five files. The page references them by exact filename, so do not rename them.

## 3. Create the site repository

On GitHub, create a **public** repository named exactly
`<your-github-username>.github.io`. The name is what makes GitHub Pages serve it
at that address; any other name serves from a subpath instead.

Then, from the `site` folder:

```
git init
git add .
git commit -m "Portfolio site with Cincinnati 311 case study"
git branch -M main
git remote add origin https://github.com/<your-github-username>/<your-github-username>.github.io.git
git push -u origin main
```

In the repository: **Settings > Pages > Source > Deploy from a branch**, branch
`main`, folder `/ (root)`. First publish takes a minute or two.

Your site is then at `https://<your-github-username>.github.io`.

## 4. Check it before you send the link anywhere

- Open it on a phone. The layout is responsive but look anyway.
- Press Tab from the top. The skip link should appear first, then the nav.
- Confirm all five images load. A broken image on a data portfolio is worse
  than no image.
- Print to PDF. The print stylesheet drops the nav and prints link targets.
- Run the page through the WAVE or Lighthouse accessibility check.

## Adding the next project

Copy `cincinnati-311.html` to a new filename, replace the content, and duplicate
the `<article class="card">` block in `index.html`.

Keep the card headline a **finding**, not a topic. "A city service fails every
summer" earns a click. "Cincinnati 311 analysis" does not.

## What this deliberately does not have

- **No analytics or tracking.** Nothing to disclose, nothing to consent to, and
  one less thing that can leak.
- **No webfonts or CDN.** The system font stack renders instantly and cannot fail
  because someone else's server is down.
- **No framework.** Two HTML files and one stylesheet will still work in five
  years with no maintenance. A build pipeline will not.
