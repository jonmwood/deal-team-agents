# Deal Team: instructions for ChatGPT, Codex and other AI agents

This folder is a team of four AI agents that help a first-time buyer screen and research small businesses for sale. The files are a Claude plugin, but they're plain Markdown. This file tells any other agent (ChatGPT, Codex, and other tools that read `AGENTS.md`) how to run them.

## Where everything lives

| What | File |
|---|---|
| Guided setup (the interview, plus both templates at the end) | `skills/setup/SKILL.md` |
| Run the whole team on one business | `skills/diligence/SKILL.md` |
| The screener (the Pokédex) | `agents/deal-screener.md` |
| The mentor (Gandalf) | `agents/deal-mentor.md` |
| The researcher (Professor Oak) | `agents/analyst.md` |
| The growth strategist (Batman) | `agents/growth-strategist.md` |
| The user's buy box and profile (created by setup) | `my/buy-box.md`, `my/about-me.md` |
| Deal work, one folder per business | `deals/` |

Each agent file starts with a short header between `---` lines (its name, description and the tools it expects). The text after that header is the agent's instructions.

## What to do

**Start here.** If `my/buy-box.md` doesn't exist or still has `[BRACKETS]`, the user hasn't been set up yet. When they say anything like "set me up", "get started" or "setup", or try to screen a listing before setup, follow `skills/setup/SKILL.md` step by step: a short interview, one question at a time, then write `my/buy-box.md` and `my/about-me.md` from the templates at the end of that file.

**Screen one listing** ("screen this listing", a pasted link or listing text): act as the screener. Spawn a subagent whose instructions are the body of `agents/deal-screener.md`, give it the listing, and return its verdict block. If you can't spawn subagents, follow that file yourself.

**Run the whole team** ("run diligence on...", "work this deal", "run the team on this business"): follow `skills/diligence/SKILL.md`. Each time it says to run an agent:

- **Spawn a subagent for that role,** with the body of that role's file in `agents/` as its instructions, and pass it the files the step names.
- **Run the researcher and the growth strategist at the same time,** as two separate subagents. Don't share one's output with the other: they're meant to work blind to each other.
- **Wait for both** before the mentor's second pass.
- **If you can't spawn subagents,** play each role yourself, one at a time, re-reading only that role's file before you start it. Then tell the user in your final report that the roles shared one context, so the screener's no-memory rule and the blind research were weaker than designed.

## Rules for every role (never break these)

- **No agent makes the buy, pass or negotiate call.** The user decides.
- **No agent contacts anyone:** no broker emails, no inquiry forms, no NDA requests. The user sends their own questions.
- **No invented numbers.** A gap is a question or "not stated", never an estimate passed off as a fact.
- **Each role writes only its own file** in `deals/<business>/`.
- **`my/` and `deals/` hold the user's private numbers.** Never publish or upload them anywhere.
