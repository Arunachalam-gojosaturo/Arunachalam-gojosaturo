# Setup checklist

## What's already done
- `dark.svg` / `light.svg` — banner built from your photo. Portrait is a
  Floyd–Steinberg dithered dot-matrix, contrast-boosted and background-segmented,
  fading in once when the page loads. Info panel has your real details, dotted
  leaders, a pulsing LIVE badge, and an `@ARC` handle pill.
- `.github/workflows/snake.yml` — contribution snake workflow, dark + light,
  slate-grey empty cell so it doesn't disappear on GitHub's dark background.
- `README.md` — assembled with banner, stats, snake, and badges wired to your
  real GitHub username, LinkedIn, Instagram, and AUR profile.

## Scope note — read this
The master prompt's Phase 1 also specifies a second layer: ~900 "traveler" dots
that morph between three logos via optimal-transport matching, looping
continuously after the intro. That piece is genuinely fragile (it's the part
the prompt itself calls "the wall you'll hit") and needs your three chosen
logos as clean reference art to trace. I built the dense portrait + scattered
fade-in intro, which is the harder and more important half, but left the
logo-morph loop out rather than rush it. If you want it, tell me which three
logos/marks to use and I'll do that as a follow-up pass.

## Things you need to do by hand

1. **Upload the SVGs to your profile repo**
   - Repo must be named `Arunachalam-gojosaturo/Arunachalam-gojosaturo`, branch `main`.
   - Copy `dark.svg`, `light.svg`, `README.md`, and the `.github/` folder into it.

2. **Create a GitHub token (for self-hosted stats)**
   - Settings → Developer settings → Tokens (classic) → Generate new (classic)
   - Scope: `repo` · Expiration: No expiration
   - Copy it immediately — GitHub only shows it once. Never paste it anywhere public.

3. **Self-host github-readme-stats** (avoids the shared instance's rate limits)
   - Fork `anuraghazra/github-readme-stats`
   - Go to vercel.com → sign up with GitHub → Hobby (free) → Add New Project → import the fork
   - Add environment variable `PAT_1` = the token from step 2 → Deploy
   - Once deployed, swap the stats URLs in `README.md` from
     `github-readme-stats.vercel.app` to your own Vercel instance URL.

4. **Enable Actions permissions for the snake workflow**
   - In the **repo's** Settings (not your account settings) → Actions → General
     → Workflow permissions → **Read and write permissions** → Save.
   - Push to `main` or run the workflow manually once to generate the `output`
     branch. The snake image in the README will 404 until this branch exists.

5. **Verify in a browser, not just by eye**
   - The intro animation and LIVE pulse are CSS/SMIL — GitHub's renderer and
     browsers show them; static image viewers won't.
   - If a change "doesn't seem to show up," it's almost always the CDN cache —
     hard refresh or append `?v=2` to the raw URL before assuming it's broken.

## File size
`dark.svg` and `light.svg` are ~610 KB each — under the 900 KB–1 MB range the
prompt flags as the normal cost of this technique.
