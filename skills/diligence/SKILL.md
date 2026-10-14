---
name: diligence
description: Run the whole deal team on one business, in order - screener, mentor, then researcher and growth strategist side by side, then mentor again. Use for "/deal-team:diligence <listing>", "run the team on this business", "work this deal". Takes a listing URL, pasted listing text, or a description. Produces a folder in deals/ with the screen, the mentor's read and walk-away line, both sets of findings, and the mentor's advice. Never makes the buy / pass / negotiate call and never contacts anyone.
---

# Diligence: run the deal team on one business

You (the main session) are the coordinator. The four agents do the work; you hand each one its inputs, in order, and pass files between them. Every handoff is a file in `deals/<slug>/`, so each agent starts fresh and reads exactly what it needs.

**Input:** $ARGUMENTS (a listing URL, pasted listing text, or a description of the business).

## Step 0: set up

0. **If `my/buy-box.md` doesn't exist yet, or still has unfilled `[BRACKETS]`, stop and tell the user to run setup (`/deal-team:setup` in Claude, or "set me up" in ChatGPT) first.** Screening against a blank rule is guessing.
1. Pick a short slug for the business (e.g. `acme-hvac`). Check `deals/` for an existing folder or a line in `deals/log.md` first. If it's already there, this is an update: reuse the folder, don't create a second one.
2. Create `deals/<slug>/` and save the raw input to `deals/<slug>/listing.md`.

## Step 1: the screener (the Pokédex)

Run the **deal-screener** agent on the listing (in Claude the agents are named `deal-team:deal-screener`, `deal-team:deal-mentor`, `deal-team:analyst` and `deal-team:growth-strategist`). Save its verdict block to `deals/<slug>/screen.md` and add one line to `deals/log.md`: date · business · asking price · verdict · reason.

- **DROP or LOG-ONLY:** stop here. Tell the buyer the verdict and the deciding rule. Only continue if they say to anyway.
- **PROMOTE:** continue.

## Step 2: the mentor's read (Gandalf, pass 1)

Run the **deal-mentor** agent: "Pass 1 on `deals/<slug>/`. Write your read to `mentor-read.md` and your numbered, tagged questions to `questions.md`. Write the master number and walk-away line before anything is researched."

Show the buyer the walk-away line before moving on. It's the most important sentence in the whole run, because it was written before the data.

## Step 3: research and growth, side by side (Professor Oak + Batman)

Run both agents **at the same time**, each told exactly which file it owns:

- **analyst:** "Answer every question tagged `research` in `deals/<slug>/questions.md`. Write only `deals/<slug>/findings-research.md`."
- **growth-strategist:** "Answer every question tagged `growth` in `deals/<slug>/questions.md`. Write only `deals/<slug>/findings-growth.md`."

They can't see each other's work, on purpose: each answers its own questions without leaning on the other's conclusions. Questions tagged `ask-seller` go to neither. They're for the buyer to send.

## Step 4: the mentor's advice (Gandalf, pass 2)

Run the **deal-mentor** agent again: "Pass 2 on `deals/<slug>/`. Read both findings files and write `mentor-advice.md`: did the walk-away line fire, what changed, the questions still for the seller, and the decision frame."

## Step 5: report back

Tell the buyer, briefly:

1. The screener's verdict.
2. The master number and whether the walk-away line fired (yes / no / can't tell until the seller answers question N).
3. The top 2-3 risks after the research.
4. The `ask-seller` questions, in priority order.
5. Where everything lives: `deals/<slug>/`.

## Rules for the whole chain

- **Nobody makes the buy / pass / negotiate call.** Not the agents, not you. The buyer decides.
- **Nobody contacts anyone.** No broker emails, no inquiry forms, no NDA requests. The buyer sends the seller questions themselves.
- **No invented numbers anywhere.** A gap is a question, not an estimate.
- **Each agent writes only its own file.**
