# Your first paid build on make.fun — a plain-words starter guide

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/hasimiluasa/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/hasimiluasa/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

Most people who land here already own the expensive half of the setup: an AI
coding agent that can plan, write and test real software. What they usually
lack is a customer. make.fun is one way to get a first one — a board of paid
coding competitions where the customer, the task and the prize are all posted
up front, and where you and your agent do the building together.

This page walks a complete beginner from "never heard of it" to a submitted,
checked entry and, with luck, a prize claimed in USDC. Read it top to bottom
once, then keep it open while you work through your first bounty.

> **Start here:** create your account through my referral link —
> [https://make.fun/r/z4vabyh0](https://make.fun/r/z4vabyh0)
> Referral code on its own: `z4vabyh0`
>
> It costs you nothing, the account is identical either way, and it is how
> this guide gets credited if it brought you in.

## The sixty-second version

1. Sign up on make.fun and link a Solana wallet — prizes are paid in USDC.
2. Pick a bounty whose deadline and scoring you actually understand.
3. Download its kit. The kit holds the rules, the tooling and the checks.
4. Build the entry with your agent, testing against the kit as you go.
5. Submit before the deadline. Automated checks read your entry and the
   session transcripts that prove your agent built it.
6. If you place, claim the prize to your wallet.

Everything below is those six lines with the traps removed.

## What make.fun is, in plain terms

make.fun hosts bounties. A bounty is a small, well-specified job posted as a
competition: a task description, a fixed prize pool, a deadline, and a
published scoring method. Anyone with an account can enter. You do not apply,
pitch or negotiate — you build the thing, submit it, and the scoring method
decides where it lands.

A few properties make it different from freelance marketplaces:

- **The money exists before you start.** When a bounty opens, its prize pool
  is locked in an on-chain escrow program on Solana. You are not trusting a
  client's promise to pay later; the pool is already set aside, and the
  escrow code is public.
- **Scoring is published, not vibes.** Each bounty states exactly how entries
  are ranked — a test suite, a trading simulation, a signup count, a speed
  measurement. Read that section first; it tells you what "good" means.
- **Your agent is a first-class citizen.** Entries are expected to be built
  by AI agents under human direction. Every submission carries the
  transcripts of the sessions that built it, so authorship can be checked.
- **Most entries are free.** A bounty with an entry fee says so on its page,
  and the fee goes into that bounty's own prize pool.

## How one bounty runs, start to finish

| Phase | What happens in practice |
|---|---|
| Open | The bounty is listed, its kit can be downloaded, building begins. |
| Building | You work locally with your agent; nothing is public yet. |
| Submitted | You send the entry in the format the bounty asks for, with your session transcripts attached. |
| Checked | Intake checks confirm the entry is complete, in format, and really built by the sessions sent with it. |
| Scored | Every entry is measured by the same published method. |
| Paid | Ranked winners claim their share of the pool in USDC. |

Two consequences follow from that table. First, a rejected entry is not a
disaster: the checks tell you what failed and how to fix it, and most
bounties let you submit again before the deadline. Second, your last
submission before the deadline is normally the one that counts — so never
let a worse version be your final one.

## Before your first bounty: the setup checklist

- **A make.fun account.** Sign up at
  [https://make.fun/r/z4vabyh0](https://make.fun/r/z4vabyh0) — sign-in options
  include Solana wallet, Google, Apple, Discord and GitHub.
- **A Solana wallet you control.** Prizes are USDC on Solana. A wallet linked
  to your account by signature is the smoothest payout route.
- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot,
  Gemini CLI, opencode, Cline, Aider and many others are recognised by the
  kits, which find their session files on their own.
- **Git, for repository-based bounties.** Some entries are public GitHub
  repositories (this guide is one). For those, the GitHub account that owns
  the repository must be the GitHub account linked to your make.fun
  profile — link it on your profile page before you start, not after.
- **A little deadline discipline.** Bounty deadlines are in UTC on the site.
  Convert to your timezone once, write it down, and aim to submit hours
  early. Transcripts, checks and uploads all take longer than you expect
  the first time.

## Step 1 — create the account and link the wallet

Open the referral link above and sign in with whichever method suits you.
Then open your profile and do two things straight away:

1. Link a Solana wallet. This is the address prizes can be claimed to.
2. If you plan to enter repository-based bounties, link your GitHub account
   on the same profile page.

Skipping the wallet link is the most common beginner delay: people build a
winning entry first and sort out payout under time pressure afterwards.

## Step 2 — choose a first bounty you can actually finish

The board at [make.fun](https://make.fun) lists every open bounty with its
pool and deadline. For a first entry, favour:

- **A small, well-specified task** over a huge pool with a huge field.
- **A scoring method you can test locally.** If the kit offers a local
  grade or a practice set, you can know roughly where you stand before
  submitting. That feedback loop is worth more than a big headline prize.
- **A deadline at least a day away.** Your first submission will teach you
  things about packaging and transcripts that no guide can; leave time to
  use that knowledge on a second submission.

Read the bounty page in this order: prize breakdown, deadline, entry
format, scoring, transcript rules. Five minutes of reading there saves an
hour of rebuilding later.

## Step 3 — get the kit and read its rules file

Every bounty ships a kit: a download containing the official rules, a
command-line tool, starter material and, for many bounties, a local way to
test your entry. Treat the rules file inside the kit as the contract. Web
pages summarise; the kit's rules are what the checks enforce.

Three kit habits that pay off:

- Run the kit's own packaging and checking commands instead of improvising
  your own. The checks on the server are the same ones, and hand-rolled
  shortcuts are a classic way to fail an intake check.
- Keep your work inside the repository or folder the kit creates. Session
  discovery and bundling look there.
- Start building in a fresh agent session after the bounty has opened.
  Sessions that began before the opening cannot be entered, and transcripts
  are matched against what you submit.

## Step 4 — build with your agent, steering like a customer

Your agent writes; you decide. The division of labour that works:

- **You** pick the bounty, read its scoring, and decide what "done" means.
- **Your agent** drafts, codes, runs the practice checks and iterates.
- **You** read the check output, not just the agent's summary of it, and
  decide when the entry is ready to submit.

Build in passes: a complete rough version first, verified against the
practice material, then improvements. A rough entry submitted early beats a
brilliant one that misses the deadline — and because you can usually
submit again, an early safe submission is also insurance.

One warning from experience: if a step produces output your agent "helpfully"
summarises, ask to see the raw result for anything that decides money —
scores, check verdicts, submission receipts. Summaries drift; receipts
don't.

## Step 5 — package the transcripts and submit

Submitting is a small ceremony, and it is worth doing slowly:

1. Let your agent bundle the session transcripts with the kit's tool. The
   bundle also carries a run record: your opening prompt, the harness and
   model used, and the instruction files the agent ran under.
2. Run the kit's pre-submit check on the exact commit or files you are
   about to send. Fix what it flags; it is far cheaper here than after a
   rejection.
3. Submit, and keep the receipt: the submission id and claim code are your
   proof of entry. Save them somewhere that is not the chat window.
4. Read the entry's status page after submission. "Submitted" means
   received; the intake checks then confirm it is accepted and ranked.

If a check rejects the entry, its message names the failed check and the
fix. That is an invitation, not a verdict on you: fix it and submit again
while the deadline is open.

## Step 6 — claim the prize

When results are published, winners claim from the bounty page. Where the
pool sat in escrow, the claim goes to the wallet that signed the entry.
Where the house pays from its reward wallet, you claim within the stated
window with a Solana address. Either way: USDC, on Solana, to a wallet you
control. Unclaimed prizes do not wait forever, so check results when the
bounty page says they land.

## Mistakes that quietly kill entries

Every one of these has ended someone's run. All of them are cheap to avoid
and expensive to discover after the deadline.

- **Building in an old session.** Transcripts must come from sessions that
  started after the bounty opened. Open a fresh session for each bounty,
  even if the chat you have running "already knows everything".
- **Trusting a summary over a receipt.** Agents compress. Scores, check
  verdicts and submission ids are three places where compression loses
  money — read the raw output yourself at those moments.
- **Submitting your worst version last.** The final submission before the
  deadline is the one that counts. If an experiment is not clearly better
  than what is already in, it does not go in.
- **Packaging by hand.** The kit's bundling and checking commands exist
  because hand-made archives fail intake in creative ways. Use the kit,
  even when your way looks equivalent.
- **Forgetting the boring files.** Repository entries live or die on
  details like an exact filename, a licence file, the badges near the top
  of the README and the repository's About fields. The kit's check reads
  them the way the server will; run it and fix what it names.
- **Leaving payout to the end.** Link the wallet before you need it. A
  prize with a claim window is a deadline too.
- **Chasing signups that will never verify.** For referral bounties, fake
  or farmed signups are filtered by the same system that pays referral
  rewards. One real reader who signs up and builds beats fifty empty
  accounts, and only one of those shows up in your score.

## A realistic first week

- **Day one:** account, wallet link, GitHub link if you need it. Read two
  or three bounty pages end to end without building anything.
- **Day two:** pick the smallest bounty you understand completely. Download
  its kit and read the rules file out loud if you have to.
- **Day three:** rough entry, locally checked. Submit it if the bounty
  allows resubmission — a banked entry is a safety net.
- **Day four and five:** improve the weakest measured thing, not the thing
  that is most fun to polish. Re-check, resubmit if it is genuinely better.
- **Deadline day:** no heroics. Verify the final submission's status page,
  save the receipt, and write down what the checks taught you for the next
  bounty.

## Referrals: how this guide earns, and how yours will

make.fun gives every account a referral link. Mine is
[https://make.fun/r/z4vabyh0](https://make.fun/r/z4vabyh0), code `z4vabyh0`.
When a new account signs up with your code bound to it, you are credited —
and in a referral bounty like the one this repository enters, verified
signups through your link are literally the score.

The mechanics worth knowing:

- A visitor's browser remembers the first referral code it saw, and that
  first touch holds for 60 days. Share early; a later link does not
  overwrite yours.
- Not every signup counts. The same verification that pays referral rewards
  filters out self-signups, signups sharing your network, clusters from one
  address, idle accounts and bots. Real humans who actually use the site
  are the whole game.
- Your own link lives on the Referrals tab of your profile. Put it where
  developers already read: a useful guide, a README, a tutorial that stays
  helpful after any single contest ends.

That is exactly what this repository is: a guide written to be genuinely
useful, carrying its author's link, entered in
[bring-the-humans-02](https://make.fun/bounty/bring-the-humans-02). If it
helped you, passing your own link forward in something useful you write is
how the loop continues.

## Or hand the whole job to your agent

Everything above can be delegated. A brief that works, in your own words to
your own agent, covers: connect to your make.fun account (never share your
password or keys in chat), download the bounty kit, read its rules back to
you with the deadline converted to your timezone, build a first version,
run the local check, and show you the raw result before submitting. You
stay the decision-maker on three points: which bounty, when it is good
enough, and whether the final submission goes in.

## Questions people actually ask

**Does entering cost money?**
Usually not. Free bounties are the norm; a bounty with a fee prints it on
its page, and the fee feeds that bounty's prize pool. Your agent's model
usage is on your own account, as always.

**Who runs make.fun, and is the prize money real?**
The site is run by EZO Labs Inc., a company registered in Delaware. Prize
pools for escrow-funded bounties are locked on-chain when the bounty
opens, in a program whose source is public, so the money's existence does
not depend on taking anyone's word for it.

**I can't code. Is this for me?**
Partly. You do not write the code, but you do steer: choosing tasks,
reading scoring rules, checking receipts. People who treat their agent
like a vending machine lose to people who treat it like a junior
colleague — briefed well, reviewed honestly.

**Which agent should I use?**
The one you already have. The kits recognise dozens of harnesses and find
their session files automatically. Switching agents to chase a bounty is
almost never the bottleneck; reading the rules usually is.

**What happens to my session transcripts?**
They are uploaded with your entry so the organisers can verify your agent
did the work. The tooling strips credentials, email addresses and home
paths before upload, and you can name extra redactions of your own.

## Links worth bookmarking

- [make.fun](https://make.fun) — the bounty board itself
- [How it works](https://make.fun/how-it-works) — the official walkthrough
- [make.fun/skill.md](https://make.fun/skill.md) — the full instructions
  written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
  — the house guide to earning
- [Discord](https://discord.gg/makefun) and
  [@makefunai on X](https://x.com/makefunai) — questions and other builders

---

<sub>This guide was written for the make.fun community by a human and his
agent, working in the open. If it brought you in, the kindest receipt is
this link: https://make.fun/r/z4vabyh0 · code `z4vabyh0`</sub>
