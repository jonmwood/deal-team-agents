# The deal team

Four AI agents that help a first-time buyer screen and research small businesses for sale, plus a guided setup and one command that runs the whole team. Built in [Claude Code](https://code.claude.com/docs/en/overview) by Jon ([@thelong.view](https://www.instagram.com/thelong.view/)), a dad of four buying his first business.

**Works in Claude Cowork, Claude Code and the ChatGPT desktop app**, with a lighter version for ChatGPT on the web. Pick your app below.

**[Download the latest version (.zip)](https://github.com/jonmwood/deal-team-agents/releases/latest/download/deal-team-agents.zip)**

---

## Meet the team

| | Agent | What it does | What it never does |
|---|---|---|---|
| **The Pokédex** | `deal-screener` | Reads a listing and checks it against your buy box, rule by rule: pass, fail or unverified | Guesses. If the listing doesn't say, it's "unverified." It also has no memory on purpose, so it can't fall for a deal it liked yesterday |
| **Gandalf** | `deal-mentor` | Thinks like a retired private equity partner. Before any research, writes the one number that decides the deal and where you walk away, then the questions. Comes back at the end with his advice | Makes the buy or pass call. That's yours |
| **Professor Oak** | `analyst` | Answers the research questions like a Big Four consultant: industry, labor, real estate, comparable sales | States a number without a source. "Not found" is an allowed answer; a guess isn't |
| **Batman** | `growth-strategist` | Your head of growth: how customers find this kind of business, what one costs to win, and the playbook the owner isn't running yet | Spends a dollar, runs an ad, or contacts anyone |

## How they work together

```
listing
  └─> Pokédex: does it clear your rules?            (most listings stop here, and that's the point)
        └─> Gandalf, pass 1: the read, the walk-away line, the questions
              ├─> Professor Oak: research questions  ┐  at the same time,
              └─> Batman: growth questions           ┘  blind to each other
                    └─> Gandalf, pass 2: what the research changed, what to ask the seller
                          └─> you decide
```

Questions only the seller can answer never go to research. They become your list for the broker.

## Get started (about 15 minutes)

Pick the app you use. Every path ends the same way: a short interview that writes your buy box, then the team is ready.

### Claude Cowork or the Claude app (easiest)

1. In Claude, open **Customize → Plugins → Add → Add marketplace**.
2. Enter `jonmwood/deal-team-agents`.
3. Find **Deal Team** in the list and add it.
4. Start a **Cowork** task in a folder on your computer (your buy box and deal work are saved there), then type `/deal-team:setup` or just say "set up my deal team."

To get updates later, open the marketplace in **Customize → Plugins** and select **Check for updates**, or turn on **Sync automatically**.

### Claude Code

Install it as a plugin, then use it in any folder:

```
/plugin marketplace add jonmwood/deal-team-agents
/plugin install deal-team@deal-team-agents
/deal-team:setup
```

Want a copy you can edit? Download the .zip above (or `git clone https://github.com/jonmwood/deal-team-agents.git`), then start Claude Code in your working folder with `claude --plugin-dir path/to/deal-team-agents` and type `/deal-team:setup`.

### ChatGPT desktop app (Codex)

1. Download the .zip above and unzip it.
2. In the ChatGPT desktop app, open the `deal-team-agents` folder as a local project and choose **Codex**.
3. Say "Set me up."

Codex reads `AGENTS.md`, which tells it where the agents live and to give each role its own subagent.

### ChatGPT on the web (lighter version)

1. Create a **Project** in ChatGPT.
2. Paste the text in [`chatgpt/project-instructions.md`](chatgpt/project-instructions.md) into the project's instructions.
3. Upload these six files to the project: `skills/setup/SKILL.md`, `skills/diligence/SKILL.md`, and the four files in `agents/`.
4. Say "Set me up." At the end, ChatGPT hands you your buy box and profile as documents. Add both to the project's files.

A web project can't save to a folder, and the four agents only run separately if your plan includes ChatGPT Work with subagents. Otherwise one ChatGPT plays all four roles in turn, which works, but loses some of the separation that makes the team careful.

### What works where

| | Claude Cowork | Claude Code | ChatGPT desktop (Codex) | ChatGPT web Project | Claude chat |
|---|---|---|---|---|---|
| Guided setup | ✅ | ✅ | ✅ | ✅ you save the files | ✅ you save the files |
| Four separate agents | ✅ | ✅ | ✅ subagents | Only with ChatGPT Work | ❌ one Claude plays every role |
| Saves to a folder on your computer | ✅ | ✅ | ✅ | ❌ | ❌ |

## Use it

Run the whole team on one business:

- **Claude:** `/deal-team:diligence https://www.example-broker.com/listing/12345`
- **ChatGPT:** "Run diligence on https://www.example-broker.com/listing/12345"

Or call one agent at a time:

- "Use the deal-screener on this listing: [paste it]"
- "Ask the deal-mentor for a read on this business: [describe it]"
- "Have the analyst research what HVAC service businesses in [your area] sell for"
- "Ask the growth-strategist how residential pest control companies win customers"

Everything lands in `deals/<business>/` in your working folder, with a one-line log of every listing in `deals/log.md`.

## Make it yours

- **Start with your buy box** (`my/buy-box.md`). Most of the team's judgment comes from your written rules. Run setup again any time to change them.
- **Edit the agents freely.** Each one is a plain text file in `agents/`: who it is, how it works, and what it's never allowed to do. Edit your own copy (see "Want a copy you can edit?" above) so an update doesn't overwrite your changes.
- **They remember.** The mentor, analyst and growth strategist keep notes between runs in your working folder, under `.claude/agent-memory/`. The screener doesn't, on purpose.
- **Your numbers stay private.** `my/` and `deals/` live in your working folder on your computer. In this repo they're git-ignored; if you work in a folder that's your own git repo, add them to its `.gitignore` before pushing it anywhere public.

## Ground rules

- **None of these agents makes the buy or pass call.** They inform it. You decide.
- **They can be wrong.** Check any number before you rely on it, especially one that came from the seller.
- **This isn't financial, legal or tax advice.** Before you sign anything, talk to a lender, a CPA and a deal attorney.
- **They never contact brokers or sellers.** You send your own questions.
- **Running them uses your Claude or ChatGPT usage**, and the research agents search the web.

---

The agent files were written with Claude in Claude Code and edited by Jon. MIT license, so take them, change them, share them. If they help, I'd love to hear about it on Instagram: [@thelong.view](https://www.instagram.com/thelong.view/).
