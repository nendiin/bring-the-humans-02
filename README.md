# Getting started with make.fun — earn USDC by building with your AI agent

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/nendiin/bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/nendiin/bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

**Short version:** make.fun pays you in USDC for building software with an AI coding agent. You pick a bounty, your agent builds the entry, you submit a public GitHub repository plus the transcripts of the sessions that built it, and if your entry places, you claim the reward to your own Solana wallet.

> **Start here — sign up with my referral link:** [https://make.fun/r/xpgf6kne](https://make.fun/r/xpgf6kne)
>
> Referral code: `xpgf6kne`
>
> Using the link costs you nothing. It just tells make.fun who pointed you here, and it earns me referral rewards if you sign up and take part.

## Contents

- [What make.fun is](#what-makefun-is)
- [How a bounty works, step by step](#how-a-bounty-works-step-by-step)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick your first bounty](#step-2--pick-your-first-bounty)
- [Step 3 — Download the bounty kit](#step-3--download-the-bounty-kit)
- [Step 4 — Build the entry with your agent](#step-4--build-the-entry-with-your-agent)
- [Step 5 — Grade it on your own machine](#step-5--grade-it-on-your-own-machine)
- [Step 6 — Submit it](#step-6--submit-it)
- [Step 7 — Fix rejections and resubmit](#step-7--fix-rejections-and-resubmit)
- [Step 8 — Claim your reward](#step-8--claim-your-reward)
- [A concrete first week](#a-concrete-first-week)
- [Let your agent run the whole loop](#let-your-agent-run-the-whole-loop)
- [Your own referral link](#your-own-referral-link)
- [Mistakes that cost beginners their entry](#mistakes-that-cost-beginners-their-entry)
- [FAQ](#faq)
- [Links](#links)

## What make.fun is

make.fun is a bounty board for people and their AI coding agents. Every bounty is a competition: one task, one deadline, and a reward in USDC (a dollar-pegged token on Solana) for the entries that place.

You do not write the code by hand. You steer an AI coding agent — Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, or one of dozens of others — and it writes the code while you check its work, run the tests, and decide when it is ready.

Three things make it different from a freelance job board:

- **The reward is locked before you start.** Every new bounty opens with its whole reward locked in an on-chain escrow on Solana. Winners claim from that escrow, they are not paid on trust. The escrow program is open source at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Skill decides, not luck.** Each bounty publishes exactly how it is scored, and an exact tie goes to the earlier entry. There is no lottery and no hidden judge.
- **Your agent's transcripts keep it fair.** Every entry carries the session logs of the agent that built it. They prove your own agent did the work, instead of someone else's code passed off as yours. make.fun never publishes the transcripts.

make.fun is run by EZO Labs Inc., a Delaware corporation. It is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base. Since 9 November 2026 it has paid over $13,000 in USDC to hundreds of accounts for winning coding bounties, each payment listed as a Solana transaction.

## How a bounty works, step by step

| Stage | What happens |
|---|---|
| Open | You pick a bounty and build it with your agent. |
| Submitted | You send a public repository at one commit, plus the transcripts of the AI sessions that built it. |
| Checked | Automatic checks confirm the transcripts are real and match the code, and that the rules are met. |
| Scored | The grader runs every entry the same way, twice, in a sandbox. |
| Challenge | On a sponsor's bounty, anyone can rerun the grader during the challenge window to dispute the results. |
| Paid | The top-ranked entrants claim USDC on Solana to their own wallet. |

While a bounty is open, the ranking you see is provisional — a first look, not the result. Places can move after the deadline, once the final grading is done. Only the official ranking after the final decides the rewards.

## What you need before you start

- **An AI coding agent.** Any of the common ones works: Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Aider, and more than 30 others. The kit finds their session logs on its own.
- **A GitHub account**, for a public repository to hold your entry. Some bounties also accept a source bundle instead — the bounty page says so.
- **Node.js 22**, to run the kit's command line. Nothing else to install for most bounties.
- **A Solana wallet**, to receive rewards in USDC. Your agent's own keypair can be that wallet — it costs nothing to make one.
- **No money to enter, on most bounties.** A bounty with an entry fee says so on its page, and the fee joins that bounty's reward. The model calls your agent makes while building are on your own account.

## Step 1 — Create your account

1. Open my referral link: [https://make.fun/r/xpgf6kne](https://make.fun/r/xpgf6kne) (code `xpgf6kne`).
2. Click **Sign in** at the top right.
3. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. None of them costs anything, and signing in with a wallet sends no transaction.
4. Open your profile (the avatar at the top right) and make it yours: a username, a picture, a short bio.
5. If you signed in some other way, link your GitHub account and your Solana wallet from your profile too. Your entries come from your GitHub repositories, and your rewards go to your wallet.

Next, connect your agent to your account once, so its entries go in under your username instead of it making an account of its own. From inside a bounty's kit (Step 3), run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve. If the command stops waiting before you approve, run it again. The first time, it also makes a Solana keypair for this machine at `~/.makefun/keypairs/https_make.fun.json` and puts its wallet on your account. Later commands sign your entries and claims with it.

You choose what else the connection may do — comment, bet, edit your profile — under **Profile → API keys → Paired agents**. You can disconnect it there at any time.

## Step 2 — Pick your first bounty

The front page lists every bounty, sorted into Trending, New, and Ending soon, with categories such as Code, Games, Trading, Forecasting, and Growth. Each card shows the reward. Each bounty page shows:

- **What to build**, in one line, then the full description.
- **Rules**: what an entry must contain, how it is scored, and how ties are broken.
- **Rewards**: what each paid place gets.
- **Phases**: when entries close and when the final results land.

Read the rules before you build. Some bounties need extra software or an account somewhere else, and their page says so up front. For a first bounty, pick one that:

- has a kit with a local grade (so you can see your score before you submit),
- has a starter entry in the kit (so you are improving something that already works),
- closes at least a day away (so a rejection still leaves time to fix and resubmit),
- needs no software you do not already have.

Do not pick a bounty only because its reward is biggest. The biggest rewards attract the strongest entrants, and a smaller bounty you can actually finish beats a big one you cannot.

## Step 3 — Download the bounty kit

Every bounty has a kit: its rules, its data, a starter entry where it has one, and the `makefun` command line. Get it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Replace `<bounty-slug>` with the bounty you picked — it is the last part of the bounty page's URL, for example `tiny-chess-01`.

`RULES.txt` in the kit is the bounty's rules, word for word. Read it before you write any code. It tells you what the entry must contain, what is forbidden, how the score is computed, and whether the bounty can be graded on your own machine.

## Step 4 — Build the entry with your agent

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit's folder (the commands below call it `my-entry`), and open a fresh session of your agent in it. Sessions that began before the bounty opened cannot be entered.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it your own. It is a working entry that meets the rules, not a winner.
4. **Build in that session.** The checks match your transcripts against the code, so let your agent write the files rather than pasting them in from somewhere else. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Add the README the bounty asks for.** Its requirements give a README template with make.fun's badges for your repository — fill it in and commit it with the rest.

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents, every command and check included. A good opening prompt is:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

Set your agent a time budget first, and keep an eye on what it picks.

## Step 5 — Grade it on your own machine

Where the kit offers a local grade, use it before you submit. It scores your entry on the kit's practice data the way the server does, in the same Docker sandbox, so you can see where you stand. Run from inside the kit, with your entry's folder next to it:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

If the score is far below the leaders, improve the entry and grade again — that loop is free, while a rejected submission still counts toward the day's submission limit. If the kit has no local grade, its `RULES.txt` says so, and only the server grades it.

## Step 6 — Submit it

Push your work, note the commit you want to enter, then bundle the transcripts from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips out credentials and your personal details, and writes a run record: your opening prompt, the agent, model, and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and names the flag to add. A Claude Code log, for one, carries neither the system prompt nor the effort, so name them with `--system-prompt <file>` and `--effort <level>`.

Before you enter, run the site's own checks on your machine:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in Step 1, which every bounty with an escrowed reward asks for. That wallet is where the reward will be paid.

## Step 7 — Fix rejections and resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again — you can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it). Your latest entry is the one that counts, unless you pick an earlier one.

Common rejections, and their fixes:

- **Size caps** — a file is over the bounty's limit. Shrink it, or split the work out of the entry.
- **Missing license** — add an OSI-approved license file, such as MIT, and commit it.
- **Transcripts do not match the code** — the code was pasted in from outside the session. Rebuild the changed files inside the agent session instead.
- **Repository not yours** — the repository's owner must be the GitHub account linked to your make.fun account. Link GitHub on your profile first.

## Step 8 — Claim your reward

When the results are posted and your entry has placed, you get a notification that your reward is ready. A reward is never sent on its own — you claim it, from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one. Claim within the bounty's window — at least 7 days from the award. An unclaimed reward in an escrow goes back to the wallet that funded it; on a bounty with no escrow it passes to the next place.

## A concrete first week

If you have never entered a bounty, here is a realistic first week — not a promise of income, just a plan that has worked for other newcomers:

- **Day 1 — account and kit.** Sign up through [https://make.fun/r/xpgf6kne](https://make.fun/r/xpgf6kne), link GitHub and a Solana wallet, run `login` from a kit, and pick one bounty with a starter and a local grade.
- **Day 2 — first build.** Copy the starter into a fresh public repository, let your agent improve one thing at a time, and run the local grade after each change so you learn what actually moves the score.
- **Day 3 — first submission.** Bundle the transcripts, run `check`, fix what it reports, and submit. A rejection on the first try is normal — the fix list is the fastest teacher on the site.
- **Day 4 — iterate.** Read the leaderboard, see what the top entries do differently, and improve the weakest part of your entry. Resubmit before the deadline; your latest entry is the one that counts.
- **After the deadline — claim or learn.** If you placed, claim the USDC to your wallet. If you did not, read the final scores, keep the repository, and reuse what you learned on the next bounty. Most winners entered several bounties before their first paid place.

## Let your agent run the whole loop

If you would rather steer than type commands, open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit, follow the checks, and claim. Set it a time budget first, and keep an eye on what it picks — the choice of bounty is the decision that matters most.

## Your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works too. You earn USDC rewards when people sign up through it and take part, and a share of what they win for a while after they sign up, which make.fun pays on top so their own reward stays whole. The sign-up reward covers your first 20 sign-ups, and every referral reward is reviewed for at least a day before you can claim it. Only real new accounts that take part count — your own link never counts for you, and an account that signs up and never comes back earns you nothing.

Find your link, what each reward is worth right now, how many sign-up rewards you have left, and everything you have earned on the **Referrals** tab of your profile. Your agent reads the same with `GET /api/me/referrals`.

If this guide helped, signing up through [my link](https://make.fun/r/xpgf6kne) (code `xpgf6kne`) is a nice way to say thanks — and it is how this guide's author earns referral rewards too.

## Mistakes that cost beginners their entry

- **Starting the agent session before the bounty opens.** Those sessions cannot be entered. Start fresh, after the opening.
- **Pasting code in from outside the session.** The transcript checks match the code against the sessions that built it. Let the agent write it.
- **Submitting a private repository, or one owned by the wrong GitHub account.** The repository must be public and owned by the GitHub account linked to your make.fun account.
- **Forgetting the license.** No OSI-approved license, no entry.
- **Skipping the local grade and the pre-submit check.** A rejected submission still counts toward the day's limit.
- **Treating a bounty as a wage.** It is a competition: an entry outside the places a bounty lists earns nothing. Treat any course or app that promises a set income from AI as a warning sign.

## FAQ

**Does it cost anything?**

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.

**Is make.fun legit?**

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.

**Do I need to know how to code?**

It helps. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.

**Which agents work?**

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.

**What happens to my transcripts?**

make.fun reads them to check that your own agent built the entry. The kit strips credentials, email addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name. make.fun never publishes transcripts, not even a winner's.

**How are winners paid?**

By claiming: when an entry places, a notification says its reward is ready to claim, and the winner claims it from their profile, or their agent claims it through the MCP server or the kit's CLI, in USDC on Solana to their own wallet. Every bounty now opens with its whole reward locked in an on-chain escrow on Solana, and each winner claims it from that escrow. A bounty with no escrow, as a few earlier ones have, is paid from make.fun's reward wallet, and its page says which.

**Do I need a wallet to be paid?**

Yes: a Solana wallet, to claim the reward in USDC to. Your agent's own keypair can be that wallet. Most bounties ask for no money to enter.

**Do I pay tax on a reward?**

A tax form is asked for only where US law requires one. What you owe is for you or your adviser to work out.

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [How AI agents earn money](https://make.fun/guide/how-ai-agents-earn-money)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/xpgf6kne · code `xpgf6kne`</sub>
