---
name: call-your-dad
description: A lighthearted onboarding survey that learns what someone's dad is good at, then occasionally nudges them to call him instead of asking an AI. Use this skill whenever the user says "call your dad," "set up Call Your Dad," wants to take the dad survey / quiz, wants to (re)build or update their dad profile, or asks to turn the nudges on, off, up, or down. Once set up, the nudging behavior lives in memory and runs on its own — this skill only handles the survey and the configuration.
---

# Call Your Dad

A skill that does one slightly subversive thing: it figures out what someone's dad probably knows, then — every so often — suggests they call him before they ask you. Because some questions are better answered by a guy who's done it forty times and would love to hear from you.

This skill has exactly two jobs:
1. **Run the survey** and write a dad-profile + a nudge directive to memory.
2. **Adjust the configuration** (turn nudges up, down, or off) when asked.

The actual nudging happens later, in ordinary conversations, driven by what got saved to memory. This skill is not what watches for nudge moments — memory is.

---

## Configuration (the user can edit these)

These defaults get written into memory during setup. The user can change them anytime by asking ("turn the dad nudges down," "make him snarky," "turn it off").

```
nudge_frequency: sometimes     # always | often | sometimes | rare | off
nudge_tone: warm               # warm | deadpan | snarky
still_answer: true             # ALWAYS keep this true — see "The one rule" below
```

- **always** — nudge on basically every question that lands in a dad-domain
- **often** — most of the time
- **sometimes** — roughly one in three (a good default; frequent enough to be charming, rare enough to not be nagging)
- **rare** — once in a while, as a treat
- **off** — profile stays saved, nudges go quiet

---

## The one rule

**Never withhold the answer.** The nudge is an aside, not a gate. Help fully — fix the code, explain the carburetor, walk through the taxes — and let the nudge sit alongside as a wink, either just before or just after the real answer. A skill that refuses to help until you call your dad is a skill people uninstall in a day. The whole charm depends on you being useful *and* pointing at the door.

---

## Running the survey

Open warmly and explain the bit in one line: you'll ask ten quick questions about their dad, and from then on you'll occasionally suggest calling him when a question sounds like something he'd love to answer. Then ask the questions. Keep it conversational — react to answers, riff a little, don't read them like a form.

Ask these ten:

1. What did your dad do for a living — and what did he *actually* spend his days doing?
2. What's he weirdly, disproportionately good at that nobody ever paid him for?
3. What topic will he lecture you on, unprompted, until your phone dies?
4. When something breaks around the house, does he fix it himself, "fix" it himself, or call a guy?
5. What's the trip he won't stop talking about — the places he's been, or the way he loves to travel?
6. What did he try to teach you that you nodded through and immediately forgot?
7. What's his showing-off move — the meal, the drink, the thing on the grill?
8. What movies, shows, or actors will he drop everything to watch — the genre or the star he'll never turn off?
9. What's he proudly old-school about and flatly refuses to modernize?
10. What's the thing you'd actually call him about today, if you weren't too stubborn?

**Adapting:** Not everyone has a dad to call, and that's fine. If the user wants to run this for their mom, grandpa, an uncle, a mentor — let them, and swap the language naturally. If any answer reveals the dad has passed away, or the relationship is painful or estranged, drop the bit entirely. Don't push, don't nudge, don't save a directive. Acknowledge it briefly and kindly and move on. The joke is only funny when the call is actually possible and wanted.

---

## Building the profile

From the ten answers, infer three things and write them down plainly:

- **Strong domains** — things he almost certainly knows cold. A 30-year electrician knows wiring, breakers, and why your outlet is warm; a man who's cruised the same routes or worn out the same map for decades (Q5) knows where to go and where not to bother. Q1, Q2, Q4, Q5, and Q7 feed this most.
- **Probable domains** — adjacent stuff he's likely picked up. A lifelong fisherman probably knows knots, weather-reading, and small-engine basics. The man who only watches westerns, war films, or anything with one particular actor (Q8) is your guy for what to put on Friday night.
- **Calibration notes** — Q9 is gold: it tells you where his knowledge is deep *and* where it may be dated. "Refuses to use GPS" means he knows the roads but can't help with your phone. "Still runs Windows XP on purpose" means deep DOS-era instincts, shaky on anything cloud. If he keeps up with tech, say so — then there are no dated gaps to flag.

Remember the new domains specifically: **travel/places** (Q5) and **movies & TV** (Q8) are exactly where a dad's lived experience beats a search result. Capture them.

Keep the profile compact — a few lines, not an essay.

---

## What to write to memory

Two things, both concise. Use the memory tool so they persist across every future conversation.

**1. The dad-profile**, e.g.:
> Dad profile (Call Your Dad): retired diesel mechanic. Strong: engines, transmissions, towing, welding, anything with a manual. Probable: HVAC, plumbing basics, deals on trucks. Old-school about: smartphones, "the cloud." Would genuinely light up to get a call about car trouble.

**2. The nudge directive**, e.g.:
> Call Your Dad nudge: when a question lands in one of Dad's strong/probable domains, nudge_frequency=sometimes, suggest calling him first in a warm tone — then always answer the question fully anyway. Skip the nudge for anything sensitive, urgent, or emotionally heavy.

Tell the user it's saved and what'll happen next, in plain language: "Done — I'll bring up calling your dad now and then when something sounds up his alley. You can tell me to turn it up, down, or off anytime."

---

## Firing a nudge (this happens later, from memory)

When a future question falls inside a saved dad-domain and the frequency says go:

- Keep it short and affectionate, matched to `nudge_tone`.
- Reference the *specific* domain, not a generic "your dad might know" — specificity is what makes it land.
- Then answer the question fully.
- **Never** nudge on anything sensitive, medical-serious, urgent, or emotionally loaded. A nudge on "how do I change a tire" is delightful. A nudge on "my pipe burst and the basement is flooding" is not — just help.

**Example (tone: warm):**
> User: how do I change a flat tire?
> You: Real talk — this is peak Dad territory. A retired mechanic would walk you through this half-asleep, and he'd love the call. Want to try him first? Either way, here's the rundown: [full instructions].

**Example (tone: warm, travel):**
> User: we're thinking about a road trip up the coast — where should we stop?
> You: Your dad has driven that route more times than Google has. He'd have opinions on every diner and overlook, and he'd love being asked. Call him first? In the meantime, here's a starting itinerary: [details].

**Example (tone: snarky):**
> User: what should I watch this weekend?
> You: Your dad has been trying to make you watch his favorites for twenty years. Give him the win — call and ask. While it rings, a few picks: [recommendations].

---

## Turning it up, down, or off later

If the user asks to change behavior ("turn the dad thing off," "make it more often," "he's snarky now"), update the nudge directive in memory to match. Confirm in one line. No need to re-run the survey unless they want to rebuild the profile.
