# GitHub Profile README Redesign — Design Spec

- **Date:** 2026-06-05
- **Repo:** `ut42tech/ut42tech` (GitHub profile README)
- **Status:** Approved (design phase)

## 1. Background & Problem

The current profile README is information-dense and hard to read:

- A tech-stack badge wall of ~50 `shields.io` badges across 8 categories.
- A long `history` section listing Awards, International activity, Community & Teaching, and Industry experience in full detail.

The new portfolio site **ut42tech.com** (the `hp` submodule) now aggregates all of this — About, full tech stack, Works, SNS, Blogs, Press — in one place. The README no longer needs to carry every detail.

## 2. Goal

Refresh the README into a **slim, attractive, "student-engineer with a bit of flair" front door**: it conveys identity + current focus, then sends the reader to the portfolio site for everything else. Target: readable in ~15 seconds.

## 3. Non-goals

- Not a full résumé. Awards / career / works detail lives on ut42tech.com.
- No exhaustive technology list. Curated icons only.
- No change to the portfolio site itself.

## 4. Audience

- **Primary:** recruiters / hiring managers (Japan) + fellow engineers and the tech community.
- **Secondary:** anyone arriving from the portfolio site or social links.

## 5. Direction (decided via visual brainstorming)

| Axis | Decision |
|------|----------|
| World / aesthetic | **Terminal / hacker** — evolves the existing `$ whoami` convention, much lighter |
| Richness | **Balanced + streak** — typing header, core sections, GitHub stat cards incl. streak. Neither minimal nor maximal |
| Accent | **Green** (`#7EE787` / `#2EA043`) on dark terminal background (`#0D1117`) |
| Language | **English primary** `README.md` + **Japanese** `README.ja.md` (mirror); both slimmed; cross-linked |

## 6. README.md Structure (top → bottom)

1. **Header** — centered **Readme Typing SVG** animating name ⇄ tagline (`Takuya Uehara` ⇄ `Design × Technology, for the best UX`). Directly below: a **Profile Views (Visitors)** badge. Top of file links to `README.ja.md`.
2. **`$ whoami`** — 3 short lines:
   - Software Engineer & Designer @ Nagasaki University · Setozaki Lab.
   - Master's student — researching generative AI × spatial computing.
   - `# I work end-to-end: design, frontend, backend, infra.`
3. **`$ cat now.md`** — 3 bullets (current focus, not a past-achievement list):
   - 🔬 Researching a communication-augmentation platform (gen-AI × XR)
   - 🛠 Building & running **tec-nova platform** — Turborepo · Hono/CF Workers · Next.js
   - 🌱 Running **ChoTech**, Nagasaki's student-engineer community
4. **`$ ls ~/stack`** — curated **skillicons** icon row + caption `# full stack & tools → ut42tech.com`
5. **`$ neofetch --github`** — **GitHub stats card** + **top-langs** (compact) + **streak**, green/transparent theme
6. **Portfolio CTA** — a single prominent **Portfolio** badge → `https://ut42tech.com`, with one caption line: `# everything else — works, awards, career, writing`

Explicitly **not** present: social link row, awards/history section, the multi-category badge wall.

## 7. Components (exact URLs / params)

All are URL-driven images — no build step. Reference values below; colors/params are adjustable.

- **Typing SVG (header):**
  `https://readme-typing-svg.demolab.com/?font=Fira+Code&weight=600&size=26&pause=1000&color=7EE787&center=true&vCenter=true&width=620&height=55&lines=Takuya+Uehara;Design+%C3%97+Technology%2C+for+the+best+UX`
- **Visitors / Profile Views:**
  `https://komarev.com/ghpvc/?username=ut42tech&label=Profile+Views&color=2ea043&style=flat`
- **Tech stack icons (skillicons):**
  `https://skillicons.dev/icons?i=ts,python,cs,swift,react,nextjs,threejs,tailwind,nodejs,unity,blender,figma,aws,cloudflare,docker&perline=10`
- **GitHub stats card (existing self-hosted endpoint):**
  `https://readme-stats.ut42tech.com/api?username=ut42tech&show_icons=true&hide_border=true&include_all_commits=true&count_private=true&theme=transparent&title_color=7EE787&icon_color=7EE787`
- **Top languages:**
  `https://readme-stats.ut42tech.com/api/top-langs/?username=ut42tech&hide_border=true&layout=compact&langs_count=6&theme=transparent&title_color=7EE787`
- **Streak:**
  `https://github-readme-streak-stats.herokuapp.com/?user=ut42tech&hide_border=true&background=00000000&ring=7EE787&fire=7EE787&currStreakLabel=7EE787&sideLabels=C9D1D9&dates=8B949E&currStreakNum=FFFFFF&sideNums=FFFFFF&longestNum=FFFFFF&longestStreakLabel=7EE787`
- **Portfolio CTA badge:**
  `https://img.shields.io/badge/Portfolio-ut42tech.com-2ea043?style=for-the-badge&logo=vercel&logoColor=white` → links to `https://ut42tech.com`

## 8. Tech-stack icon set (curated, ordered)

`ts, python, cs, swift, react, nextjs, threejs, tailwind, nodejs, unity, blender, figma, aws, cloudflare, docker` (15 icons, `perline=10`). Order and membership are adjustable; goal is a representative cross-section (languages → frontend → backend/runtime → XR/3D → design → cloud), not completeness.

## 9. Rendering approach on GitHub

- **Centered images** via `<div align="center">` for: typing SVG, visitors badge, stack icons, stat cards, portfolio CTA.
- **Section headers** as `### \`$ whoami\`` / `### \`$ cat now.md\`` / `### \`$ ls ~/stack\`` / `### \`$ neofetch --github\`` (inline-code command style). This matches the current file's convention and renders reliably on GitHub.
- **`whoami` / `now` content** as short bullet lists or line-broken text.
- **Optional flourish (not required):** an ` ```ansi ` fenced block to get a colored green prompt for `whoami`. Skip if it complicates maintenance.

## 10. README.ja.md (Japanese mirror)

- Same structure and components as `README.md`.
- Prose lines (`whoami`, `now`, CTA caption) written in Japanese.
- Typing SVG Japanese line optional (e.g., `デザインとテクノロジーで、最高のUXを`).
- Links back to `README.md` (English) at the top; `README.md` links to it.

## 11. Content moved OUT of README → portfolio site

- The full 8-category tech badge wall.
- `history`: Awards, International, Community & Teaching, Industry.
- Social link row (X, note, YouTube, Wantedly) — all reachable from the site.

## 12. Maintenance notes

- Stats reuse the **existing self-hosted** `readme-stats.ut42tech.com` (github-readme-stats mirror) already in use.
- Streak via `github-readme-streak-stats.herokuapp.com`; typing via `readme-typing-svg.demolab.com`; visitors via `komarev.com/ghpvc`; icons via `skillicons.dev`; badge via `shields.io`.
- All external; no local build. If any third-party service is flaky long-term, it can be swapped or self-hosted later.

## 13. Acceptance criteria (Definition of Done)

- `README.md` renders the 6 sections in §6 with working images and the green terminal theme.
- No badge wall, no `history` section, exactly one portfolio link as the outbound CTA.
- `README.ja.md` mirrors the structure in Japanese; the two files cross-link.
- The page reads top-to-bottom in ~15 seconds and images scale on mobile.

## 14. Open / adjustable later

- Icon set & order; accent theme color (green ↔ cyan/purple).
- Optionally adding a single `🏆 highlights` line under the header later (currently deferred to the site).
- The optional ANSI colored-prompt experiment.
