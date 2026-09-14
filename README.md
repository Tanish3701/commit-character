# Commit Character

Turn any public GitHub profile into an RPG character sheet. Enter a username, and your commit history, languages, stars, followers, and account age get translated into a class, a level, five attributes, a set of "battle scars," and a trio of equipped artifacts (your top repos).

Pure novelty, fully client-side, nothing stored anywhere.

## Try it

Live demo: **[tanish3701.github.io/commit-character](https://tanish3701.github.io/commit-character/)**

Or just download `index.html` and open it in any browser — no build step, no install.

## How it reads your history

Everything is pulled live from GitHub's public REST API in your browser:

| Character trait | Derived from |
|---|---|
| **Class** | Your most-used language across non-fork repos (e.g. Python → *Serpent Sage*, Rust → *Ironclad Alchemist*) |
| **Level & XP** | Stars, forks, followers, repo count, account age, and recent push activity |
| **Attributes** (STR/DEX/CON/INT/CHA) | Stars → power, push frequency → agility, account age → endurance, language diversity → intellect, followers → charisma |
| **Battle scars** | Earned badges like *Bug slayer* (recent fix commits), *Streak walker* (longest consecutive push streak), *Veteran*, *Polyglot* |
| **Equipped artifacts** | Your top 3 repos by star count |

Recent-activity stats (streaks, fix counts) are drawn from GitHub's public events feed, which only covers roughly the last 90 days — so those numbers reflect recent momentum, not full history.

## Sharing

Each character card can be:
- **Downloaded** as a high-resolution PNG, rendered with the actual page fonts so it looks the same as on screen
- **Shared to X** with a pre-filled post summarizing the character

## Tech

Single self-contained `index.html` — no framework, no build step, no backend.

- [GitHub REST API](https://docs.github.com/en/rest) (unauthenticated, client-side `fetch`)
- [html-to-image](https://github.com/bubkoo/html-to-image) for PNG export
- Google Fonts: Cinzel, Cinzel Decorative, Crimson Pro, Space Mono

## Running locally

No dependencies to install. Just open the file:

```bash
git clone https://github.com/Tanish3701/commit-character.git
cd commit-character
open index.html   # or double-click it, or drag it into a browser tab
```

Because it calls the GitHub API directly from the browser, it needs to run as a real page (a `file://` tab or a hosted URL) — sandboxed previews that block outbound network requests won't be able to fetch profile data.

## Limitations

- GitHub's unauthenticated API allows 60 requests/hour per IP address. Testing repeatedly in a short window can trip that limit.
- Only public activity is visible — private repos and contributions don't factor in.
- Recent-activity badges (streaks, fix counts) are bounded by GitHub's ~90-day public events window.

## License

MIT — do whatever you'd like with it.
