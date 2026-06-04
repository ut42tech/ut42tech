# GitHub Profile README Redesign — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the dense profile README with a slim, terminal-styled front door (English `README.md` + Japanese `README.ja.md` mirror) that defers all detail to ut42tech.com.

**Architecture:** Two cross-linked Markdown files. Each uses `### \`$ command\`` section headers for the terminal feel and URL-driven images (typing SVG, visitors, skillicons, GitHub stat cards) for the visual flair. No build step, no automated unit tests — this is content; verification is URL-resolution + structure greps + a visual render check.

**Tech Stack:** GitHub-Flavored Markdown + inline HTML (`<div align="center">`, `<img>`, `<sub>`, `<a>`). External image services: readme-typing-svg.demolab.com, komarev.com, skillicons.dev, readme-stats.ut42tech.com (self-hosted), github-readme-streak-stats.herokuapp.com, img.shields.io.

**Branch:** `readme-redesign` (already created from `main`).

**Spec:** `docs/superpowers/specs/2026-06-05-readme-redesign-design.md`

---

## File Structure

| File | Responsibility | Action |
|------|----------------|--------|
| `README.md` | English-primary profile front door | **Overwrite** (currently ~140 lines → ~55 lines) |
| `README.ja.md` | Japanese mirror, same structure/components | **Overwrite** |

Both files share the identical header, stack-icons, stats, and CTA blocks (language-neutral). Only the `whoami` / `now.md` prose and the CTA caption differ by language. The typing-SVG header stays English in both files (Fira Code has no Japanese glyphs; keeping it English avoids tofu and keeps the brand line consistent).

---

## Task 1: Rewrite `README.md` (English, slim terminal)

**Files:**
- Modify (overwrite): `README.md`

- [ ] **Step 1: Read the current README for context**

Run: `cat README.md` (or open it). Confirm you are replacing the dense version (whoami → neofetch → `top` → ~50-badge `stack` wall → `history` with Awards/International/Community/Industry → `ssh` links). The new version keeps only: header, `whoami`, `now.md`, `stack` (icons), `neofetch`, and a single Portfolio CTA.

- [ ] **Step 2: Overwrite `README.md` with the exact content below**

````markdown
<div align="center">

<img alt="Takuya Uehara — Design × Technology, for the best UX" src="https://readme-typing-svg.demolab.com/?font=Fira+Code&weight=600&size=26&pause=1000&color=7EE787&center=true&vCenter=true&width=620&height=55&lines=Takuya+Uehara;Design+%C3%97+Technology%2C+for+the+best+UX" />

<img alt="Profile Views" src="https://komarev.com/ghpvc/?username=ut42tech&label=Profile+Views&color=2ea043&style=flat" />

<sub>🇯🇵 日本語版 → <a href="./README.ja.md">README.ja.md</a></sub>

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

Expected: every line starts with `200`. If `readme-stats.ut42tech.com` returns non-200, the self-hosted endpoint is down — fall back to `https://github-readme-stats.vercel.app` with the same query string. If streak returns non-200 transiently, re-run once.

- [ ] **Step 4: Visual render check**

Render the Markdown the way GitHub would and eyeball it:
- Quick: open `README.md` in VS Code preview (`Cmd+Shift+V`) — confirms structure, links, and that images load.
- GitHub-accurate (optional): `pipx run grip README.md` then open `http://localhost:6419`.

Expected: centered animated typing header + Profile Views badge; four `$ ...` sections; a single row of tech icons; stats + top-langs side by side with the streak below; one green **Portfolio** badge at the bottom. No badge wall, no awards list.

- [ ] **Step 5: Commit**

```bash
git add README.md
git commit -m "feat: redesign profile README into slim terminal front door

Replace the dense layout (50-badge stack wall + full awards/career
history) with a terminal-styled README: typing header, whoami, now.md,
icon stack, GitHub stats + streak, and a single Portfolio CTA. All
detail now lives on ut42tech.com.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>"
```

---

## Task 2: Rewrite `README.ja.md` (Japanese mirror)

**Files:**
- Modify (overwrite): `README.ja.md`

- [ ] **Step 1: Read the current Japanese README for context**

Run: `cat README.ja.md`. Confirm you are replacing the dense Japanese version with a mirror of the new `README.md` — same components, Japanese prose for `whoami` / `now.md` / CTA caption, and the top link pointing to `README.md` (English).

- [ ] **Step 2: Overwrite `README.ja.md` with the exact content below**

````markdown
<div align="center">

<img alt="Takuya Uehara — Design × Technology, for the best UX" src="https://readme-typing-svg.demolab.com/?font=Fira+Code&weight=600&size=26&pause=1000&color=7EE787&center=true&vCenter=true&width=620&height=55&lines=Takuya+Uehara;Design+%C3%97+Technology%2C+for+the+best+UX" />

<img alt="Profile Views" src="https://komarev.com/ghpvc/?username=ut42tech&label=Profile+Views&color=2ea043&style=flat" />

<sub>🇬🇧 English → <a href="./README.md">README.md</a></sub>

</div>

### `$ whoami`

- ソフトウェアエンジニア & デザイナー @ **長崎大学** · 瀬戸崎研究室
- 生成AI × 空間コンピューティングを研究する修士学生
- `# デザイン・フロントエンド・バックエンド・インフラまで一気通貫`

### `$ cat now.md`

- 🔬 生成AI × XR のコミュニケーション拡張プラットフォームを研究
- 🛠 **[tec-nova platform](https://github.com/ut42tech/tecnova-platform)** を開発・運用 — Turborepo · Hono/CF Workers · Next.js
- 🌱 長崎の学生エンジニアコミュニティ **[ChoTech](https://github.com/nu-chotech)** を運営

### `$ ls ~/stack`

<div align="center">

<img alt="Tech stack" src="https://skillicons.dev/icons?i=ts,python,cs,swift,react,nextjs,threejs,tailwind,nodejs,unity,blender,figma,aws,cloudflare,docker&perline=10" />

</div>

<sub># 技術スタックの全体 → <a href="https://ut42tech.com">ut42tech.com</a></sub>

### `$ neofetch --github`

<div align="center">

<img alt="GitHub stats" height="165" src="https://readme-stats.ut42tech.com/api?username=ut42tech&show_icons=true&hide_border=true&include_all_commits=true&count_private=true&theme=transparent&title_color=7EE787&icon_color=7EE787" />
<img alt="Top languages" height="165" src="https://readme-stats.ut42tech.com/api/top-langs/?username=ut42tech&hide_border=true&layout=compact&langs_count=6&theme=transparent&title_color=7EE787" />

<img alt="GitHub streak" src="https://github-readme-streak-stats.herokuapp.com/?user=ut42tech&hide_border=true&background=00000000&ring=7EE787&fire=7EE787&currStreakLabel=7EE787&sideLabels=C9D1D9&dates=8B949E&currStreakNum=FFFFFF&sideNums=FFFFFF&longestNum=FFFFFF&longestStreakLabel=7EE787" />

</div>

---

<div align="center">

<sub># 制作物・受賞・経歴・発信のすべて</sub>

<a href="https://ut42tech.com"><img alt="Portfolio — ut42tech.com" src="https://img.shields.io/badge/Portfolio-ut42tech.com-2ea043?style=for-the-badge&logo=vercel&logoColor=white" /></a>

</div>
````

- [ ] **Step 3: Verify parity and cross-link**

Run:

```bash
# Cross-links resolve to each other
grep -q 'href="./README.md"' README.ja.md && echo "JA→EN link OK"
grep -q 'href="./README.ja.md"' README.md && echo "EN→JA link OK"
# Image component set is identical across both files (same 6 image hosts)
for host in readme-typing-svg komarev skillicons readme-stats.ut42tech.com streak-stats shields.io; do
  a=$(grep -c "$host" README.md); b=$(grep -c "$host" README.ja.md)
  echo "$host  EN=$a  JA=$b"
done
```

Expected: both link lines print OK; for each host the `EN` and `JA` counts match (typing 1, komarev 1, skillicons 1, readme-stats 2, streak 1, shields 1).

- [ ] **Step 4: Commit**

```bash
git add README.ja.md
git commit -m "feat: mirror slimmed terminal README in Japanese

Rewrite README.ja.md to match the new README.md structure with
Japanese prose for whoami/now and a single Portfolio CTA.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>"
```

---

## Task 3: Final acceptance check & branch handoff

**Files:** none (verification only)

- [ ] **Step 1: Confirm the dense content is gone (acceptance criteria)**

Run:

```bash
# No leftover badge wall (only ONE shields badge total = the Portfolio CTA)
echo "shields badges in README.md: $(grep -c 'img.shields.io' README.md) (expect 1)"
# No history/awards section survived
grep -iE "Award|Hackathon|Internship|President's|JSET|IIIT|Wantedly|YouTube|note\.com" README.md \
  && echo "!! leftover detail found — remove it" || echo "history/social fully removed OK"
# Exactly one outbound portfolio link present
echo "portfolio links in README.md: $(grep -c 'ut42tech.com' README.md) (expect >=2: stack caption + CTA)"
```

Expected: 1 shields badge; "history/social fully removed OK"; portfolio referenced (stack caption + CTA).

- [ ] **Step 2: Final visual pass on both files**

Open both `README.md` and `README.ja.md` in preview. Confirm they read top-to-bottom in ~15 seconds, images scale, and the green terminal theme is consistent. Spot-check on a narrow window (mobile-ish) that the stats images wrap gracefully.

- [ ] **Step 3: Branch is ready to integrate**

Run: `git log --oneline main..readme-redesign` — expect the two `feat:` commits (plus the earlier `chore:`/`docs:` commits). The branch is now ready for the **superpowers:finishing-a-development-branch** skill to merge to `main` (or open a PR). The real-world final check is viewing the rendered profile on GitHub after merge, since GitHub is the only environment that renders the profile exactly.

---

## Self-Review (against the spec)

**Spec coverage:**
- §6.1 Header (typing SVG + visitors + JA link) → Task 1 Step 2 (header block) ✓
- §6.2 `$ whoami` → Task 1 Step 2 ✓
- §6.3 `$ cat now.md` → Task 1 Step 2 ✓
- §6.4 `$ ls ~/stack` icons → Task 1 Step 2 ✓
- §6.5 `$ neofetch` stats+langs+streak → Task 1 Step 2 ✓
- §6.6 Portfolio CTA → Task 1 Step 2 ✓
- §7 exact component URLs → reproduced verbatim in Task 1/2 + checked in Task 1 Step 3 ✓
- §8 curated 15-icon set → identical skillicons URL in both files ✓
- §9 rendering approach (`### \`$ cmd\`` headers, centered HTML images) → followed ✓
- §10 README.ja.md mirror → Task 2 ✓
- §11 removed content (badge wall, history, social row) → enforced in Task 3 Step 1 ✓
- §13 acceptance criteria → Task 3 ✓

**Placeholder scan:** No TBD/TODO; both files given in full; all commands concrete. ✓

**Consistency:** Icon list, stats params, accent hex (`7EE787`/`2ea043`), and the typing header are byte-identical between `README.md` and `README.ja.md`. Cross-links point at each other (`./README.ja.md` ↔ `./README.md`). ✓

**Note on TDD:** A profile README has no unit-test target. The TDD analog used here is: define the expected outcome (URL resolves / structure grep), run the check, confirm it passes, commit. This is intentional and complete for a content deliverable.
