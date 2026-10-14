---
name: setup-team
description: Guided first-run setup for the deal team. Interviews a new user in plain English (about 10 minutes), writes their buy box to my/buy-box.md and their buyer profile to my/about-me.md, then offers a test run on a real listing. Use for "/setup-team", "set me up", "help me fill in my buy box", "configure the agents", or whenever my/buy-box.md is missing or still has blanks. Re-run any time to update.
---

# /setup-team: set up your deal team

You're walking someone through their first setup. Assume they're smart, new to buying businesses, and possibly new to Claude Code. Your job is to turn a short, friendly interview into two files the agents read on every run:

- `my/buy-box.md`: the rules a business has to clear (built from `templates/buy-box.md`)
- `my/about-me.md`: who they are, so the advice fits them (built from `templates/about-me.md`)

Both live in `my/`, which is git-ignored, so their numbers stay on their machine.

## How to run the interview

- **Start by saying what's about to happen,** in two lines: about 12 questions, about 10 minutes, and "not sure" is always an acceptable answer.
- **One question at a time.** Wait for the answer. Use multiple-choice options where the answers fall into a few buckets; open questions where they don't.
- **Explain jargon the first time it comes up,** in one plain sentence: SDE (seller's discretionary earnings, roughly what the owner takes home), asking price, debt coverage, SBA loan.
- **Define, don't assert.** When you explain a term or flag a conflict, say what the term means or what to check. Don't add claims about what most buyers do, what lenders require, or what a state licenses; you'd be stating facts you haven't sourced. Point them to the person who'd know (a lender, a broker, an attorney).
- **Never recommend numbers as advice.** You can offer example ranges to react to, clearly labeled as examples. If they're unsure about money or financing, record "not sure yet" and tell them that's a great first question for a lender.
- **"Not sure" or "skip" is fine.** Write `TBD` for that slot and tell them what it means: the screener will mark that rule UNVERIFIED on every listing until they fill it in.
- **Don't ask for anything you don't need.** No account numbers, no exact net worth. A cash range is plenty.
- **If `my/` already exists,** this is an update: read the current files first, show what's there, and only ask about what they want to change.

## The questions

### Part 1: about you (fills `my/about-me.md`)

1. **Who you are:** "In a sentence or two, who are you and why do you want to buy a business?"
2. **Experience:** "What have you done for work? And what haven't you done yet that running a business might need, like managing people, running sales, or reading a P&L?" (Their gaps are as useful as their strengths: the mentor coaches to them.)
3. **Time:** "How many hours a week can you give the search right now? And after you buy, do you want to run it full-time, part-time with a manager, or mostly hands-off?"
4. **Money (rough):** "Roughly how much cash could you put in, as a range? And how do you expect to pay for the rest: an SBA loan, seller financing, cash, partners, or not sure yet?"
5. **Where:** "Where's home base, and how far would you drive to a business regularly? Would you consider one with no physical site, like an online business?"

### Part 2: your buy box (fills `my/buy-box.md`)

6. **Price:** "What's the lowest and highest asking price you'd look at?" If they're unsure, offer to come back to it after question 4, or mark it TBD. Don't derive a price from their cash for them; that's lender math.
7. **Owner's role:** "How hands-on are you willing to be? Should the screener fail businesses where the owner *is* the business, like the owner does all the sales or all the skilled work?"
8. **Industries:** "Any industries you're drawn to? Any you'd never touch?" Then: "Any regulated categories to rule out, like medical, licensed professional practices, or anything that needs multi-year approvals?"
9. **Business age:** "What's the youngest business you'd consider, in years in operation?" Offer options like 3, 5 or 10 years, as examples.
10. **Repeat demand:** "How much do you care that customers come back on their own, like contracts, memberships or a regular replacement cycle? Must-have, nice-to-have, or doesn't matter?"
11. **How strict:** "Each listing gets checked against 6 rules. How many should it pass, with zero fails, before the team does a deep dive? Most people start at 4 of 6." (4 is this template's default, not a rule of thumb from anywhere else.)
12. **Your sweet spot (optional):** "If you could describe your ideal business in one line, what is it?" Then offer the green flags in the template and ask if they want to add any.

## Write the files

1. **Show a summary first:** their six rules as a short table, and their profile in five lines. Ask: "Anything to change before I save it?"
2. Create `my/` if needed. Write `my/about-me.md` from `templates/about-me.md` and `my/buy-box.md` from `templates/buy-box.md`, replacing every `[BRACKET]` with their answer or `TBD`. Keep the templates' structure and wording around the brackets, and drop the template's "This is the template" note.
3. **Leave the templates untouched.** They're the blank copies for next time.
4. Read both files back and confirm there are no `[BRACKETS]` left (a `TBD` is fine).

## Test drive

Offer it, don't force it:

"Want to see it work? Paste a link to a business for sale, from BizBuySell, a broker's site, or an alert email, and I'll run the screener on it."

- Run the **deal-screener** agent on it and show the verdict. Explain the result in two lines, especially what UNVERIFIED means (the listing didn't say, so the screener refused to guess).
- If it PROMOTEs, offer the full team: `/diligence <the same link>`.
- If they don't have a listing handy, skip it.

## Close

End with a short "here's what you've got":

- **Your rules:** `my/buy-box.md`. **Your profile:** `my/about-me.md`. Edit either any time, or run `/setup-team` again.
- **Screen a listing:** "Use the deal-screener on this listing: [paste]."
- **Run the whole team:** `/diligence [listing link]`.
- **Your deal work** lands in `deals/`, and none of it, nor `my/`, gets pushed if they publish the repo.
- **The ground rule:** the agents never make the buy or pass call. They help you make it.
