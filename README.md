# The deal team

Four AI agents that help a first-time buyer screen and research small businesses for sale, plus one command that runs them in order. Built in [Claude Code](https://code.claude.com/docs/en/overview) by Jon ([@thelong.view](https://www.instagram.com/thelong.view/)), a dad of four buying his first business.

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

## Set it up (about 15 minutes)

1. **Install Claude Code:** [setup guide](https://code.claude.com/docs/en/setup).
2. **Get this folder:** download the .zip above and unzip it, or `git clone https://github.com/jonmwood/deal-team-agents.git`.
3. **Open it in Claude Code:** `cd deal-team-agents`, then `claude`.
4. **Type `/setup-team`.** It interviews you in plain English (about 10 minutes, "not sure" is always fine), then writes your buy box and a short profile the agents read before every run. At the end it offers a test run on a real listing.

Prefer to do it by hand? Copy `templates/buy-box.md` and `templates/about-me.md` into a folder called `my/` and fill in every `[BRACKET]`.

## Use it

Run the whole team on one business:

```
/diligence https://www.example-broker.com/listing/12345
```

Or call one agent at a time:

- "Use the deal-screener on this listing: [paste it]"
- "Ask the deal-mentor for a read on this business: [describe it]"
- "Have the analyst research what HVAC service businesses in [your area] sell for"
- "Ask the growth-strategist how residential pest control companies win customers"

Everything lands in `deals/<business>/`, with a one-line log of every listing in `deals/log.md`.

## Make it yours

- **Start with your buy box** (`my/buy-box.md`). Most of the team's judgment comes from your written rules. Re-run `/setup-team` any time to change them.
- **Edit the agents freely.** Each one is a plain text file in `.claude/agents/`: who it is, how it works, and what it's never allowed to do.
- **They remember.** The mentor, analyst and growth strategist keep notes between runs in `.claude/agent-memory/`. The screener doesn't, on purpose.
- **Your numbers stay private.** `my/`, `deals/`, `research/` and the agents' memory are git-ignored, so pushing your copy of this repo won't publish them.

## Ground rules

- **None of these agents makes the buy or pass call.** They inform it. You decide.
- **They can be wrong.** Check any number before you rely on it, especially one that came from the seller.
- **This isn't financial, legal or tax advice.** Before you sign anything, talk to a lender, a CPA and a deal attorney.
- **They never contact brokers or sellers.** You send your own questions.
- **Running them uses your Claude usage**, and the research agents search the web.

---

The agent files were written with Claude in Claude Code and edited by Jon. MIT license, so take them, change them, share them. If they help, I'd love to hear about it on Instagram: [@thelong.view](https://www.instagram.com/thelong.view/).
