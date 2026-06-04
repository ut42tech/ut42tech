# GitHub Profile README Redesign — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the dense profile README with a single slim, terminal-styled English front door that defers all detail to ut42tech.com.

**Architecture:** One Markdown file (`README.md`). It uses `### \`$ command\`` section headers for the terminal feel and URL-driven images (typing SVG, visitors, skillicons, GitHub stat cards) for the visual flair. No build step, no automated unit tests — this is content; verification is URL-resolution + structure greps + a visual render check.

**Tech Stack:** GitHub-Flavored Markdown + inline HTML (`<div align="center">`, `<img>`, `<sub>`, `<a>`). External image services: readme-typing-svg.demolab.com, komarev.com, skillicons.dev, readme-stats.ut42tech.com (self-hosted), github-readme-streak-stats.herokuapp.com, img.shields.io.

**Branch:** `readme-redesign` (already created from `main`).

**Spec:** `docs/superpowers/specs/2026-06-05-readme-redesign-design.md`

> **Update (2026-06-05):** Bilingual decision reversed — the README is **English-only** this round and `README.ja.md` is **deleted**. Japanese readers are served by the (Japanese) portfolio at ut42tech.com.

> **Update 2 (2026-06-05):** Design softened to a **neutral / clean theme** — green accent removed; header cycles 3 typing lines (`Hi there, I'm Takuya Uehara 👋` → `Full-stack Dev & Design` → motto) in gray `#808080`; `neofetch` reverts to `theme=transparent`; **Profile Views + Portfolio become subtle flat badges in a bottom footer** (top visitors badge and large CTA removed); whoami reads *AI agent × spatial computing*. The green component URLs in Task 1 below are superseded by the shipped `README.md`, which is canonical.

---

## File Structure

| File | Responsibility | Action |
|------|----------------|--------|
| `README.md` | Single English profile front door | **Overwrite** (currently ~140 lines → ~50 lines) |
| `README.ja.md` | Former Japanese mirror | **Delete** (`git rm`) |

`README.md` carries: an animated header (typing SVG + visitors badge), `whoami`, `now.md`, an icon `stack`, a `neofetch` stats block (stats + top-langs + streak), and one Portfolio CTA. Everything else (full stack, awards, career, social) lives on ut42tech.com.

---

## Task 1: Rewrite `README.md` (English, slim terminal)

**Files:**
- Modify (overwrite): `README.md`

- [ ] **Step 1: Read the current README for context**

Run: `cat README.md`. Confirm you are replacing the dense version (whoami → neofetch → `top` → ~50-badge `stack` wall → `history` with Awards/International/Community/Industry → `ssh` links). The new version keeps only: header, `whoami`, `now.md`, `stack` (icons), `neofetch`, and a single Portfolio CTA. No Japanese cross-link (the JA file is removed in Task 2).

- [ ] **Step 2: Overwrite `README.md` with the exact content below**

````markdown
<div align="center">

<img alt="Takuya Uehara — Design × Technology, for the best UX" src="https://readme-typing-svg.demolab.com/?font=Fira+Code&weight=600&size=26&pause=1000&color=7EE787&center=true&vCenter=true&width=620&height=55&lines=Takuya+Uehara;Design+%C3%97+Technology%2C+for+the+best+UX" />

<img alt="Profile Views" src="https://komarev.com/ghpvc/?username=ut42tech&label=Profile+Views&color=2ea043&style=flat" />

</div>

### `$ whoami`

- Software Engineer & Designer @ **Nagasaki University** · Setozaki Lab.
- Master's student — researching **generative AI × spatial computing**.
- `# I work end-to-end: design, frontend, backend, infra.`

### `$ cat now.md`

- 🔬 Researching a communication-augmentation platform (gen-AI × XR)
- 🛠 Building & running **[tec-nova platform](https://github.com/ut42tech/tecnova-platform)** — Turborepo · Hono/CF Workers · Next.js
- 🌱 Running **[ChoTech](https://github.com/nu-chotech)**, Nagasaki's student-engineer community

### `$ ls ~/stack`

<div align="center">

<img alt="Tech stack" src="https://skillicons.dev/icons?i=ts,python,cs,swift,react,nextjs,threejs,tailwind,nodejs,unity,blender,figma,aws,cloudflare,docker&perline=10" />

</div>

<sub># full stack &amp; tools → <a href="https://ut42tech.com">ut42tech.com</a></sub>

### `$ neofetch --github`

<div align="center">

<img alt="GitHub stats" height="165" src="https://readme-stats.ut42tech.com/api?username=ut42tech&show_icons=true&hide_border=true&include_all_commits=true&count_private=true&theme=transparent&title_color=7EE787&icon_color=7EE787" />
<img alt="Top languages" height="165" src="https://readme-stats.ut42tech.com/api/top-langs/?username=ut42tech&hide_border=true&layout=compact&langs_count=6&theme=transparent&title_color=7EE787" />

<img alt="GitHub streak" src="https://github-readme-streak-stats.herokuapp.com/?user=ut42tech&hide_border=true&background=00000000&ring=7EE787&fire=7EE787&currStreakLabel=7EE787&sideLabels=C9D1D9&dates=8B949E&currStreakNum=FFFFFF&sideNums=FFFFFF&longestNum=FFFFFF&longestStreakLabel=7EE787" />

</div>

---

<div align="center">

<sub># everything else — works, awards, career, writing</sub>

<a href="https://ut42tech.com"><img alt="Portfolio — ut42tech.com" src="https://img.shields.io/badge/Portfolio-ut42tech.com-2ea043?style=for-the-badge&logo=vercel&logoColor=white" /></a>

</div>
````

- [ ] **Step 3: Verify every image URL resolves (the "test")**

Run this from the repo root:

```bash
for url in \
  "https://readme-typing-svg.demolab.com/?font=Fira+Code&weight=600&size=26&pause=1000&color=7EE787&center=true&vCenter=true&width=620&height=55&lines=Takuya+Uehara;Design+%C3%97+Technology%2C+for+the+best+UX" \
  "https://komarev.com/ghpvc/?username=ut42tech&label=Profile+Views&color=2ea043&style=flat" \
  "https://skillicons.dev/icons?i=ts,python,cs,swift,react,nextjs,threejs,tailwind,nodejs,unity,blender,figma,aws,cloudflare,docker&perline=10" \
  "https://readme-stats.ut42tech.com/api?username=ut42tech&show_icons=true&hide_border=true&include_all_commits=true&count_private=true&theme=transparent&title_color=7EE787&icon_color=7EE787" \
  "https://readme-stats.ut42tech.com/api/top-langs/?username=ut42tech&hide_border=true&layout=compact&langs_count=6&theme=transparent&title_color=7EE787" \
  "https://github-readme-streak-stats.herokuapp.com/?user=ut42tech&hide_border=true&background=00000000&ring=7EE787&fire=7EE787&currStreakLabel=7EE787" \
  "https://img.shields.io/badge/Portfolio-ut42tech.com-2ea043?style=for-the-badge&logo=vercel&logoColor=white" ; do
  code=$(curl -s -L -o /dev/null -w "%{http_code}" "$url")
  echo "$code  ${url:0:60}..."
done
```

Expected: every line starts with `200`. If `readme-stats.ut42tech.com` returns non-200, the self-hosted endpoint is down — fall back to `https://github-readme-stats.vercel.app` with the same query string. If streak returns non-200 transiently, re-run once. (Verified 2026-06-05: all `200`.)

- [ ] **Step 4: Visual render check**

Render the Markdown the way GitHub would and eyeball it:
- Quick: open `README.md` in VS Code preview (`Cmd+Shift+V`) — confirms structure, links, and that images load.
- GitHub-accurate (optional): `pipx run grip README.md` then open `http://localhost:6419`.

Expected: centered animated typing header + Profile Views badge; four `$ ...` sections; a single row of tech icons; stats + top-langs side by side with the streak below; one green **Portfolio** badge at the bottom. No badge wall, no awards list, no Japanese link.

- [ ] **Step 5: Commit** (done together with Task 2's deletion — see Task 2 Step 3)

---

## Task 2: Delete `README.ja.md` (drop the Japanese mirror)

**Files:**
- Delete: `README.ja.md`

- [ ] **Step 1: Remove the file**

```bash
git rm README.ja.md
```

- [ ] **Step 2: Confirm nothing else references it**

```bash
grep -rn "README.ja" . --include="*.md" --exclude-dir=.superpowers || echo "no references remain"
```

Expected: no references in `README.md` (the spec/plan only mention it as removed). If `README.md` still links to it, delete that `<sub>🇯🇵 …</sub>` line.

- [ ] **Step 3: Commit `README.md` rewrite + `README.ja.md` deletion together**

```bash
git add README.md README.ja.md
git commit -m "feat: redesign profile README into slim terminal front door

Replace the dense layout (50-badge stack wall + full awards/career
history) with a single English terminal-styled README: typing header,
whoami, now.md, icon stack, GitHub stats + streak, and one Portfolio
CTA. Drop README.ja.md — Japanese readers are served by ut42tech.com.
All detail now lives on the portfolio site.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>"
```

---

## Task 3: Final acceptance check & branch handoff

**Files:** none (verification only)

- [ ] **Step 1: Confirm the dense content is gone (acceptance criteria)**

Run:

```bash
# README.ja.md is gone
test ! -f README.ja.md && echo "README.ja.md removed OK"
# Only ONE shields badge total = the Portfolio CTA
echo "shields badges in README.md: $(grep -c 'img.shields.io' README.md) (expect 1)"
# No history/awards/social section survived
grep -iE "Award|Hackathon|Internship|President's|JSET|IIIT|Wantedly|YouTube|note\.com" README.md \
  && echo "!! leftover detail found — remove it" || echo "history/social fully removed OK"
# Portfolio referenced (stack caption + CTA)
echo "portfolio links in README.md: $(grep -c 'ut42tech.com' README.md) (expect >=2)"
```

Expected: README.ja.md removed; 1 shields badge; "history/social fully removed OK"; portfolio referenced ≥2.

- [ ] **Step 2: Final visual pass**

Open `README.md` in preview. Confirm it reads top-to-bottom in ~15 seconds, images scale, and the green terminal theme is consistent. Spot-check a narrow window (mobile-ish) so the stats images wrap gracefully.

- [ ] **Step 3: Branch is ready to integrate**

Run: `git log --oneline main..readme-redesign` — expect the `feat:` commit (plus the earlier `chore:`/`docs:` commits). The branch is now ready for the **superpowers:finishing-a-development-branch** skill to merge to `main` (or open a PR). The real-world final check is viewing the rendered profile on GitHub after merge, since GitHub is the only environment that renders the profile exactly.

---

## Self-Review (against the spec)

**Spec coverage** (with the 2026-06-05 English-only update applied):
- §6.1 Header (typing SVG + visitors; JA link removed) → Task 1 Step 2 ✓
- §6.2 `$ whoami` → Task 1 Step 2 ✓
- §6.3 `$ cat now.md` → Task 1 Step 2 ✓
- §6.4 `$ ls ~/stack` icons → Task 1 Step 2 ✓
- §6.5 `$ neofetch` stats+langs+streak → Task 1 Step 2 ✓
- §6.6 Portfolio CTA → Task 1 Step 2 ✓
- §7 exact component URLs → reproduced verbatim + checked in Task 1 Step 3 ✓
- §8 curated 15-icon set → skillicons URL in Task 1 Step 2 ✓
- §9 rendering approach (`### \`$ cmd\`` headers, centered HTML images) → followed ✓
- §10 (Japanese mirror) → **superseded**: Task 2 deletes `README.ja.md` ✓
- §11 removed content (badge wall, history, social row) + README.ja.md → Task 2 + Task 3 Step 1 ✓
- §13 acceptance criteria (JA cross-link bullet dropped) → Task 3 ✓

**Placeholder scan:** No TBD/TODO; file given in full; all commands concrete. ✓

**Consistency:** Icon list, stats params, accent hex (`7EE787`/`2ea043`), and the typing header are internally consistent. No remaining reference to `README.ja.md` except as a deletion target. ✓

**Note on TDD:** A profile README has no unit-test target. The TDD analog used here is: define the expected outcome (URL resolves / structure grep), run the check, confirm it passes, commit. This is intentional and complete for a content deliverable.
