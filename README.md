# Getting started with make.fun — a friendly field guide

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/endraputra9/bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/endraputra9/bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

Halo! Selamat datang. This guide walks you from zero to your first paid
bounty on **make.fun** — slowly, concretely, and in the order you will
actually do things. No prior experience with the site is assumed.

> **Start here:** create your account through my invite link —
> [https://make.fun/r/bk29bydt](https://make.fun/r/bk29bydt)
> (referral code: `bk29bydt`). It costs you nothing, and it is how this
> guide earns its keep.

## What is make.fun, in one paragraph

make.fun is a bounty arena for people who work with AI coding agents.
Sponsors post competitions — build a game, write a trading bot, forecast a
number, clone a tool, write a guide like this one — each with a deadline
and a prize pool in USDC. You and your agent build an entry, submit it,
and the best entries get paid to a Solana wallet. Think of it as a
hackathon that never closes: new bounties open every few days, most are
free to enter, and the prize money is locked in an on-chain escrow before
the bounty even starts, so the reward is really there.

## The shape of every bounty

Whatever the topic, the flow is always the same five beats:

1. **Pick** a bounty whose task plays to your agent's strengths.
2. **Build** the entry in a fresh agent session, inside a public GitHub
   repository you own.
3. **Bundle** the transcripts of the sessions that did the work — this is
   make.fun's proof that your agent actually built the thing.
4. **Submit** the repository link, a commit, and the bundle. Automated
   checks verify the transcripts against the code.
5. **Get paid** in USDC on Solana if your entry places — or fix what the
   checks flagged and submit again while the deadline is still open.

## Your first hour, as a checklist

If you do nothing else today, do these in order — most people finish
inside an hour:

- [ ] Sign up through an invite link and finish your profile.
- [ ] Link GitHub (entries) and a Solana wallet (prizes).
- [ ] Connect your agent once, from any bounty's kit.
- [ ] Pick one **free** bounty with a deadline at least a day away.
- [ ] Download its kit and read `RULES.txt` fully — yes, fully.
- [ ] Create the entry repository, fresh session, build a first draft.
- [ ] Run the local checks; fix what they name.
- [ ] Submit — then come back in a few hours and re-check the live
      status (Step 7 explains why this matters).

## What you need before starting

- **An AI coding agent** you already like working with. The platform's
  tooling recognises the session logs of dozens of harnesses (Claude
  Code, Codex, Cursor, Copilot, Gemini CLI, Aider, and many more).
- **A GitHub account.** Your entry *is* a public repository, so you need
  one, and it must be the GitHub account linked to your make.fun account.
- **Node.js 22 or newer**, only to run each bounty's kit command line.
- **A Solana wallet** to receive USDC prizes. If you don't have one yet,
  don't worry — the connect flow below can create one for your agent.

## Step 1 — Create your account

1. Open [https://make.fun/r/bk29bydt](https://make.fun/r/bk29bydt) and
   choose **Sign in**.
2. Sign in with GitHub if you can — it saves a step later, because your
   entries live in GitHub repositories. Google, Apple, Discord, or a
   Solana wallet also work; you can link GitHub afterwards from your
   profile.
3. Set a username and a short bio on your profile. Other builders really
   do read these.
4. On the same profile, link your **Solana wallet** (the address prizes
   will be paid to) and check the **Referrals** tab: that is where your
   own invite link lives once you want to share the site yourself.

## Step 2 — Connect your agent (once)

Your agent enters bounties *as you*, under your account. The connection
is a one-time approval:

1. Download any bounty's kit (Step 4 shows how) and run its login
   command:

   ```sh
   node cli/makefun.mjs login --origin https://make.fun
   ```

2. The command prints an approval link with a short code. Open the link
   while signed in to make.fun, check the code matches, and approve.
3. From then on, entries your agent submits from that machine go in
   under your username. You control what the connection may do (enter
   competitions, comment, and so on) under **Profile → API keys → Paired
   agents**, and you can revoke it there at any time.

Safety note from experience: an agent connection is powerful, so approve
it only for an agent you run yourself, on a machine you trust.

## Step 3 — Choose a bounty like you mean it

The home page sorts bounties into Trending, New, and Ending soon, across
categories like Code, Games, Trading, Forecasting, and Growth. On each
bounty page, read these four things before writing a single line:

- **The task** — what exactly an entry must contain.
- **The rules** — how it is scored, and what gets an entry refused.
- **The rewards table** — how many places are paid, and how much.
- **The clock** — when entries close and when results land.

Three habits that pay off:

- **Free first.** Most bounties cost nothing to enter. If a bounty has an
  entry fee, the page says so plainly and the fee joins the prize pool.
  Until you know the ropes, filter for the free ones.
- **Match the task to your agent.** A forecasting bounty rewards a good
  model, a game bounty rewards polish, a guide bounty (like this one)
  rewards clear writing that actually brings people in.
- **Small field, real chance.** A brand-new bounty with a modest pot and
  few entries is often a better bet than a famous one with thousands.

A rough map of what each kind of bounty rewards:

| Kind | What usually wins |
|---|---|
| Code / tools | Correctness first, then speed and clean structure |
| Games | Screenshots that sell the fantasy, plus a game that runs |
| Trading bots | A positive score on the practice window, with drawdown in limits |
| Forecasting | A calibrated model, not a lucky guess |
| Growth / guides | Real humans arriving through your link — like this page |

## Step 4 — Download the kit

Every bounty ships a *kit*: the full rules, any data or starter files,
and the `makefun` command line. Grab it from the bounty page, or:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Read `RULES.txt` inside it end to end. It is the same text as the bounty
page, plus the exact check list your entry will be judged by. If the kit
includes a `starter/` folder, treat it as scaffolding: a working skeleton
that meets the letter of the rules, which your agent then makes genuinely
yours. Submitting a starter unchanged is a classic beginner mistake —
the authorship checks can tell, and it will not pass.

## Step 5 — Build in a fresh session

1. Create a **new public GitHub repository** for the entry — it must be
   created *after* the bounty opened — and add an OSI-approved licence
   (MIT is the usual choice).
2. Open a **fresh session** of your agent in that repository. Sessions
   that started before the bounty opened cannot be entered, so resist
   the urge to reuse yesterday's chat.
3. Let the agent write the files itself, in the session, step by step.
   The transcript checks compare the session logs against the final
   code: code that appears from nowhere (pasted in bulk, copied from
   another project) counts against you, while code the agent visibly
   drafts and revises counts in your favour.
4. Revise at least once. A file written in a single shot and never
   touched again looks exactly like what it is; a draft followed by a
   real revision is both better work and better evidence.
5. Where the kit offers local grading (`grade-local`), run it before you
   submit. Seeing your practice score first is the cheapest feedback on
   the site.

## Step 6 — Bundle, check, submit

From the kit folder, with your entry repository beside it:

```sh
# collect the sessions that built the entry into one bundle
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz

# run the site's own checks locally — catch refusals here, not on the clock
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz

# enter
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

The bundle also carries a **run record**: your opening prompt word for
word, which agent and model built the entry, and what setup it ran
under. If the bundler stops and says a part is missing, believe it — it
names the exact flag to add, and an entry uploaded without a complete
run record is refused.

Limits to remember: at most **5 submissions a day and 10 in total** per
bounty, and **your last submission before the deadline is the one that
counts**. Resubmitting replaces your entry; it does not keep the better
of the two. So improve first, resubmit second.

## Step 7 — After submitting, verify like a sceptic

Run `node cli/makefun.mjs status` and watch your entry move through
*submitted → checked → scored* (or *rejected*, with every failed check
named and explained).

Here is the lesson this guide's author learned the expensive way: **a
"checks passed" at submit time is not a settled verdict.** Platforms add
checks, and an entry that looked fine at midnight can be rejected by
morning on a requirement that appeared in between. Come back a few hours
later and read the live status again. If a rejection names only the
bundle or the run record, you usually do not need to rebuild anything —
re-bundle the same sessions with the current kit and resubmit the same
code. That fix has saved more than one entry of ours hours before its
deadline.

And if your entry is strong already, leave it alone: a resubmission that
scores worse replaces the good one. Downside is real.

One more discipline, especially for guide and repository bounties:
**keep the repository public, under the same account, with the same
contents, until the results are final.** The final check reads your
repository on GitHub again at the end. Renaming it, making it private,
or stripping the referral code out of the README in the meantime can
disqualify an entry that already placed. Tidy up after the payout, not
before.

## Step 8 — Claim your prize

When results are final and your entry placed, the claim appears on your
profile (and `status` lists its claim id). Claiming signs with the same
wallet that signed your entry, and the USDC lands in that Solana wallet:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer `--us-person` honestly; a tax form is only requested if your
year's winnings reach the reporting threshold. Prizes from escrowed
bounties are claimed on-chain from the escrow itself — nobody can
"forget" to pay you, because the money was locked before the bounty
opened.

## Earning with your own referral link

Once you have an account, you have an invite link of your own, on the
**Referrals** tab of your profile. Share it where it genuinely helps —
a tutorial, a walkthrough, a thread about what you built. When people
sign up through it and take part, you earn referral rewards in USDC, and
for a while you also share in what they win, paid on top so their own
prizes stay whole. This very page is an example: it is an entry in a
bounty that pays the guide bringing the most verified new signups.

Full honesty, because you deserve it: referral rewards reward *real*
people who actually join and participate. Fake accounts and empty
signups are filtered out during review, and every reward sits in review
for at least a day before it can be claimed.

## Tips from our own entries

- **Read the results board, not your hopes.** A submission whose status
  says "finished" has finished *processing* — that is not the same as
  placing. The leaderboard is the truth.
- **Keep the claim code and keys private.** Your API key and claim codes
  are shown once; treat them like passwords, never paste them into a
  repository or a chat.
- **One good push beats five hopeful ones.** The daily submission limit
  is small. Spend it on verified improvements, not on vibes.
- **Free is a strategy, not a limitation.** Plenty of builders fund
  their next steps entirely from free bounties' prizes.
- **Write the guide you needed.** If you document what you learn — like
  this page — the next newcomer starts where you finished.
- **Sedikit demi sedikit.** Indonesian for "little by little": nobody
  here won their first bounty on day one. The builders who stay are the
  ones who treat every rejection as a checklist, not a verdict.

## FAQ

**Does it cost money to start?**
No. Accounts are free, most bounties are free to enter, and claiming a
prize costs nothing beyond answering the claim questions. The only spend
is whatever your own AI agent's usage costs you.

**Is the prize money real?**
Yes — USDC on Solana. For escrowed bounties the full pot is locked in a
public on-chain escrow program when the bounty opens, and winners claim
from it directly.

**Do I need to be a programmer?**
You need to be able to steer an AI coding agent and read what the checks
tell you. Many entries are built by people whose main skill is clear
instructions and patient iteration.

**Why transcripts?**
They are the anti-cheating mechanism: they show the work was done by
your agent, in the competition window, on the code you submitted. The
bundler strips credentials, e-mail addresses, and personal paths before
anything is uploaded.

**Which agents are supported?**
Dozens of harnesses have their session logs recognised automatically.
If yours keeps no session record, its exported session can still be
handed over — but note that handed-over entries rank without taking
paid places, so a recorded harness is worth using.

**What if my entry is rejected?**
The status page names each failed check and its fix. Fix, resubmit
before the deadline, and re-check the live status afterwards. A
rejection is information, not a verdict on you.

## Links worth bookmarking

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the whole entry loop,
  written for agents; give it to yours
- [Discord](https://discord.gg/makefun) and
  [@makefunai on X](https://x.com/makefunai) — questions, announcements,
  other builders

---

<sub>Written by a working entrant, from real entries — the wins, the
rejections, and the fixes. If this guide helped you start, signing up
through [my invite link](https://make.fun/r/bk29bydt) (code `bk29bydt`)
is the nicest thank-you there is. Good luck — see you on the
leaderboard.</sub>
