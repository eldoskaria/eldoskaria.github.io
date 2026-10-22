# eldoskaria.github.io

Portfolio site for Eldo M Skaria, live at https://eldoskaria.github.io.

Built with Jekyll, which GitHub Pages runs automatically. There's nothing to install: push a change and the site rebuilds in a minute or two.

## Add a new case study

1. Copy `case-study-template.md` into the `_work` folder and rename it, for example `_work/new-booking-api.md`. The name becomes the address: `/work/new-booking-api/`.
2. Fill in the fields at the top (title, summary, role, metrics and so on) and write the sections below them in plain Markdown.
3. Set `order` to choose its position on the home page (1 = first).
4. Commit and push. It appears on the home page and gets its own page.

You can also do this on github.com: open the `_work` folder, choose **Add file → Create new file**, paste the template, and commit.

## Edit the home page

| What | Where |
|---|---|
| Hero numbers, impact numbers, principles, capabilities, experience, quick facts, toolkit | `_data/home.yml` |
| Hero text, About text, contact text | `index.html` |
| Name, email, LinkedIn, site description | `_config.yml` |
| Colours, fonts, layout | `assets/css/site.css` |

## Folder layout

```
_config.yml            site settings
_data/home.yml         home-page content
_layouts/default.html  header, footer, page shell
_layouts/case-study.html  case-study page design
_work/*.md             one file per case study
assets/                stylesheet and icon
index.html             home page
case-study-template.md template for new case studies (not published)
```

## Keeping it at a high standard

- Lead with outcomes and numbers, then explain how you got there.
- Say what *you* decided, not just what the team did.
- Keep confidential details out: no internal system names, URLs, client names or figures you aren't allowed to share.
- Review every few months: add new work, retire weaker pieces, and update the numbers.
