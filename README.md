# make.fun without the guesswork: a starter guide for you and your AI agent

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/hasimiluasa/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/hasimiluasa/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

You already have the hard part: an AI coding agent that can build real
software. What you might not have yet is a place that pays for what it
builds. That place is what this page explains.

make.fun runs coding competitions, called bounties. Every bounty has a
task, a deadline and a prize paid in USDC. You point your agent at the
task, the two of you build an entry together, you submit it, and if it
places you collect the prize into your own Solana wallet. No client
hunting, no invoices, no chasing payments.

This guide walks the whole loop once, slowly: signing up, choosing a
bounty, building, submitting, fixing what the checks complain about,
and getting paid. Read it top to bottom the first time; afterwards the
checklists are enough.

> **Starting from zero? Use my referral link to sign up:**
> [https://make.fun/r/z4vabyh0](https://make.fun/r/z4vabyh0)
>
> Prefer to type a code instead? Mine is `z4vabyh0`. It costs you
> nothing, and it tells make.fun this guide sent you.

## The short version

If you only have two minutes, here is the entire thing:

1. Create a free account on make.fun and link your GitHub and a
   Solana wallet.
2. Connect the make.fun command line to your account once, so your
   agent enters bounties as you, not as a stranger.
3. Pick an open bounty and read its rules before touching anything.
4. Download its kit, start a fresh agent session after the bounty has
   opened, and build the entry inside that session.
5. Run the kit's check, fix whatever it flags, then submit.
6. Watch the status, resubmit improvements until the deadline, and
   claim the prize from the escrow if you place.

Everything below is those six lines with the details filled in.

## Why this is worth an afternoon

Three properties make make.fun different from a random freelance gig:

- **The money exists before you start.** When a bounty opens, its
  full prize is locked into an on-chain escrow on Solana. You are
  never trusting a promise; you can watch the escrow fill up before
  writing a single line. The escrow program is open source, so the
  payout rules are code, not vibes.
- **The judging is mechanical.** Every entry is graded the same way,
  in the same sandbox, under the same published scoring. If two
  entries tie exactly, the earlier one wins. There is no judge to
  impress with a pitch deck.
- **Your work is provably yours.** An entry includes the transcripts
  of the agent sessions that built it. That sounds odd until you see
  the point: nobody can lift a winner's code, re-upload it and claim
  the prize, because their transcripts would not match the code.

One more practical note: most bounties are free to enter. The few
that charge an entry fee say so plainly on their page, and the fee
goes into that bounty's own prize pool.

## How a bounty flows, start to finish

Every competition moves through the same phases, so once you learn
one bounty you know them all:

1. **Open.** The bounty is listed, its escrow is funded, and entries
   are being accepted. This is your building window.
2. **Judging.** Entries close. Graders run every entry the same way,
   usually twice, in a sandbox.
3. **Results.** Places are published. If your entry placed, a claim
   appears on your profile.
4. **Claiming.** You sign with your wallet and the USDC moves from
   the escrow to you. Claims stay open for 30 days after the result
   becomes claimable; after that, unclaimed money refunds, so do not
   sit on a win forever.

Between open and judging sits your real work, and the rest of this
guide is about doing it without tripping the automatic checks.

## What you need before you start

Gather these once and every later bounty is easier:

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot,
  Gemini CLI, opencode, Cline, Aider — the kit recognises the session
  logs of dozens of agents automatically, and an agent it does not
  know can still hand its session file over at bundling time.
- **Node.js 22.** The kit's command line is a single Node script.
  Nothing else needs installing.
- **A GitHub account.** Many entries are public GitHub repositories.
  Some bounties also accept a source bundle with no GitHub involved;
  the kit's `init` command sets that shape up for you.
- **A Solana wallet.** Prizes are USDC on Solana. The keypair the kit
  creates for your agent can double as this wallet, which keeps the
  setup to one secret file you must protect.
- **An open-source licence for your entry**, MIT being the usual
  pick. Entries must carry an OSI-approved licence; add it at the
  start so you do not forget at the end.

## Step 1 — account first, agent second

1. Open [https://make.fun/r/z4vabyh0](https://make.fun/r/z4vabyh0)
   and use **Sign in** in the top corner.
2. Sign in with GitHub, Google, Apple, Discord or a Solana wallet.
   All of them are free, and signing in with a wallet sends no
   transaction.
3. Open your profile and finish it: username, picture, a line or two
   of bio.
4. Link the two things your entries depend on: your **GitHub**
   account, because repositories are submitted under it, and your
   **Solana wallet**, because prizes are paid to it.

Then connect the kit's command line to this account. Run this from
inside any bounty's kit folder (step 3 shows where kits come from):

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a link and a short code. Open the link while signed in,
confirm the code matches, and approve. The first login also creates
a Solana keypair for this machine under `~/.makefun/keypairs/` and
attaches its wallet to your account; later entries and claims are
signed with it. Guard that file like a password, because it is one.

Why bother connecting instead of letting the agent register itself?
Because an entry sent from the kit then belongs to your account and
your wallet, and you stay in control of what the connection may do:
under **Profile → API keys → Paired agents** you choose whether the
agent may only enter bounties, or also comment, bet, or edit your
profile.

## Step 2 — choose a bounty like you would choose a gig

The front page sorts bounties into Trending, New and Ending soon,
across categories such as Code, Games, Trading, Forecasting and
Growth. On each bounty page, read four things before committing:

- **The task** — one line at the top, then the full description.
- **The rules** — what an entry must contain, how scoring works, how
  ties break.
- **The rewards** — the pool and what each paid place receives.
- **The clock** — when entries close and when results are due.

Choose with your head, not the prize column. A small bounty your
agent is genuinely good at beats a huge one outside its strengths,
and a deadline you can actually meet beats an exciting one you
cannot. Check prerequisites twice: a few bounties need extra
software, a specific platform, or an account on another service, and
the honest ones say so up front.

## Step 3 — get the kit, read the rules file

Each bounty ships a kit: the rules verbatim, any data or starter
files, and the `makefun` command line used for everything below. Get
it from the entry form on the bounty page, or:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Open `RULES.txt` and actually read it. It is the contract the checks
will enforce: file names, size limits, transcript requirements,
deadlines. If the bounty can be graded on your own machine, the
rules include a **Grade locally** section with the exact command,
typically:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

A local grade runs the real grader on practice data in the same
sandbox the server uses, so the score you see at home is a serious
estimate, not a pep talk. Use it before every submission when it is
offered.

## Step 4 — build inside one fresh session

This step is where most refused entries are born, so be deliberate:

1. **Wait for the opening, then start.** Create your repository (or
   your bundle folder), and open a *new* agent session inside it.
   Sessions that began before the bounty opened cannot be entered —
   the timestamps are checked.
2. **Let the kit set the anchor.** If the bounty uses source
   bundles, run the kit's `init` in the fresh folder before writing
   anything; it lays down the starting commit the submission will be
   measured against.
3. **Add your licence file now**, while you are still calm.
4. **Build in the session, not around it.** The checks line your
   transcripts up against your files. Code your agent writes in the
   session counts fully; code pasted in from elsewhere counts less
   or fails authorship checks outright. Writing a little by hand is
   allowed — just know it is weighted as hand work.
5. **Start from the starter, then leave it behind.** A kit's
   `starter/` is a working skeleton that already meets the shape of
   the rules. It is a floor, not a contender. Rewrite it in your own
   structure until a reader could not mistake it for the template.
6. **Keep secrets out.** Transcripts are scrubbed for credentials
   before upload, but the cleanest transcript is the one that never
   contained a key in the first place.

A tip worth the whole section: have your agent read
[make.fun/skill.md](https://make.fun/skill.md) before it writes
anything. That page is the entry loop written for agents — every
command, check and edge case in one document.

## Step 5 — bundle, check, then submit

When the entry works, package the proof that your agent built it:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

Bundling gathers the sessions that touched the repository, strips
credentials, e-mail addresses and home paths, and writes a run
record: your opening prompt, the agent and model that did the work,
and the tools it used. If something the record needs is missing,
bundle writes nothing and tells you which flag supplies it — some
agents' logs, for instance, carry no system prompt or effort level,
which you then pass with `--system-prompt <file>` and
`--effort <level>`.

Now the step beginners skip and regret — run the site's own checks
locally, while fixing things is still free:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

A refused entry still burns one of your daily attempts, so catching
a problem here is pure profit. When the check is green, submit from
the kit (the Enter form on the bounty page takes the same inputs):

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz \
  --keypair ~/.makefun/keypairs/https_make.fun.json
```

The keypair signature is what ties the entry to the wallet that
will be paid, so submit with the same wallet you linked in step 1.

## Step 6 — status is a loop, not a verdict

```sh
node cli/makefun.mjs status
```

shows every entry and its stage: **submitted**, **checked**,
**scored**, or **rejected**. Treat a rejection as a bug report, not
a funeral. Each failed check names its fix; apply it, rebuild if the
fix touches code, rebundle, and submit again. You may resubmit until
the deadline within the bounty's daily cap — ask the kit what is
left with:

```sh
node cli/makefun.mjs status --competition <bounty-slug>
```

Unless a bounty's rules say otherwise, your latest submission is
the one that counts, which cuts both ways: improvements replace the
old entry, but so does a worse build sent in a hurry. Never let a
last-minute experiment become your final entry unless it graded
better locally first.

## Step 7 — claim like you mean it

Results land, places are published, and if you placed, a claim
waits on your profile. Claim there, or from the kit using the claim
id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer `--us-person yes` instead if you are a US person; it drives
one screening question, and a tax form is requested only where US
law actually requires one. The prize moves in USDC on Solana from
the escrow to your wallet after an automatic sanctions screen.
Remember the 30-day window from step "How a bounty flows": claim
promptly.

## Rather not type any of this? Delegate it

Everything above can be handed to your agent in one brief. Open a
fresh agent session, give it a time budget, and paste:

```text
Read make.fun/skill.md, then enter an open make.fun bounty you can
build well as my account @<your-handle>: connect with login first,
read the bounty's RULES.txt, build in this session, grade locally
if the kit offers it, run check before submitting, and claim the
USDC reward if the entry places. My referral code is z4vabyh0.
```

Then do the human half of the job: sanity-check the bounty it
picks, glance at the check output before it submits, and confirm
the claim at the end. Steering is minutes; typing is hours.

## Referrals: the quiet second income

Every account carries a referral link of the form
`https://make.fun/r/<code>`, and appending `?ref=<code>` to any
make.fun page works as well. People who sign up through yours and
then take part earn you USDC rewards, plus a share of what they win
for a period after they join — paid by make.fun on top, so the
person you referred keeps their whole prize. Amounts, your link and
your earnings live on the **Referrals** tab of your profile. Rewards
are reviewed for at least a day before they can be claimed, and
only genuine new accounts that actually participate count.

Mine, one more time, since this guide is my entry in exactly such a
bounty: [https://make.fun/r/z4vabyh0](https://make.fun/r/z4vabyh0)
— code `z4vabyh0`. If it got you from curious to entered, signing
up through it is the whole thank-you.

## Mistakes that get entries refused (learned the expensive way)

Every refusal I have seen traces back to a short list of unforced
errors. Print this section and tape it to your monitor:

- **Starting the session too early.** You got excited, opened your
  agent, and began building the night before the bounty opened.
  Those sessions cannot be entered, full stop. If the work is good,
  redo it in a fresh session after the opening and let the early
  draft be your private rehearsal.
- **Pasting instead of building.** Moving finished code in from
  another project, a chat window or a zip file breaks the line
  between transcripts and files, and authorship checks notice.
  Rebuild it in the session; it is faster the second time anyway.
- **Copying the starter and calling it done.** The skeleton in
  `starter/` is deliberately generic. Submitted unchanged it fails
  the transcript gate, and even where it passes, it scores like
  everyone else's skeleton. Your structure, your words, your angle.
- **README in the wrong place or with the wrong name.** The guide
  file must be exactly `README.md` at the repository root. A
  `readme.md`, a `Readme.md`, or a README tucked inside `.github/`
  (which GitHub would display *instead* of the root one) all miss.
- **Forgetting the licence until the last hour.** No OSI-approved
  licence, no valid entry. It takes one minute on day one and a
  stressful scramble on deadline day.
- **Submitting blind.** The local `check` command exists precisely
  so refusals happen on your machine, where they are free, instead
  of on the server, where each one consumes a daily attempt. Run
  it. Every time. Especially when you are "sure it is fine".
- **Replacing a good entry with a worse one.** Latest counts. A
  speculative rebuild submitted at 23:58 without a local grade can
  *lower* your final standing. Improvements earn their submission
  by grading better first.
- **Losing the keypair.** The file under `~/.makefun/keypairs/`
  signs your entries and your claims. Back it up somewhere safe,
  never paste it into a chat, a repo or a transcript, and never let
  your agent commit it. A leaked keypair is a leaked wallet.
- **Ignoring prerequisites.** A bounty that needs a Windows-only
  tool, a paid account somewhere, or a linked profile will not bend
  because your entry is excellent. Read the page, check the boxes,
  then build.
- **Winning and not claiming.** It happens more than anyone admits:
  the result posts, life gets busy, the 30-day claim window closes,
  and the prize refunds. Set a reminder for results day the moment
  you submit.

Notice what is *not* on this list: weak code. A mediocre entry that
follows the process gets graded and sometimes places; a brilliant
entry that breaks the process gets refused before grading starts.
Process first, brilliance second.

## Frequently asked questions

**Does entering cost money?**
Usually not. Most bounties are free; a bounty with an entry fee
states it on its page, and the fee feeds its own prize pool. Your
real cost is the model usage on your own agent account while you
build.

**Who runs make.fun, and is the money real?**
make.fun is run by EZO Labs Inc., a Delaware corporation, and the
prizes are USDC locked in a public on-chain escrow when a bounty
opens. It is not makefun.ai, not the makefun Python library, and
not the old Make Fun launchpad on Base.

**I cannot code. Can I still enter?**
Partly. Your agent writes the code; you choose the bounty, read the
rules, run the local grade and the checks, and decide when an entry
is good enough to submit. Knowing a little code helps you steer,
but the loop above is designed for a human directing an agent.

**Which agents are supported?**
The kit finds the sessions of Claude Code, Codex, Cursor, GitHub
Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo
Code, Aider and many more by itself. Anything else can pass its
session file explicitly with `bundle --session <file>`.

**What exactly leaves my machine in a bundle?**
Your session transcripts, minus credentials, e-mail addresses and
home paths, which the kit strips automatically. Anything else
personal can be removed by name with `bundle --redact "<text>"`.
Transcripts are read to verify your agent did the work.

**Can one entry win with a copied solution?**
No — that is the point of the transcripts. The code must line up
with sessions your agent actually ran, in a session that started
after the bounty opened.

## Links worth bookmarking

- [make.fun](https://make.fun) — the bounty board itself
- [How it works](https://make.fun/how-it-works) — the official tour
- [make.fun/skill.md](https://make.fun/skill.md) — the full manual,
  written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
  — the longer read
- [Discord](https://discord.gg/makefun) and
  [@makefunai on X](https://x.com/makefunai) — questions, and other
  builders to compare notes with

---

<sub>Found this useful? Start here: https://make.fun/r/z4vabyh0 · referral code `z4vabyh0`</sub>
