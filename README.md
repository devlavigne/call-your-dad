# Call Your Dad

A [Claude Skill](https://support.claude.com/en/articles/12512180-use-skills-in-claude) that does one slightly subversive thing: it learns what your dad is actually good at, then — every so often — suggests you call *him* before you ask an AI. Because some questions are better answered by a guy who's done it forty times and would love to hear from you.

It never withholds the answer. The nudge is a wink, not a paywall.

## How it works

1. **You run a short survey.** Ten quick questions about your dad — what he did for a living, what he's weirdly good at, what he'll lecture you about until your phone dies.
2. **It builds a profile in memory.** Claude infers the domains your dad knows cold (repairs, the grill, that one road trip he's taken a hundred times) and saves a compact profile plus a nudge setting.
3. **Later, it nudges — gently.** When a future question lands in one of his domains, Claude will sometimes say "honestly, this is a phone-call-to-Dad question" — and then answer you fully anyway.

The survey is all this skill does. The nudging happens on its own afterward, driven by what got saved to memory.

## The one rule

**Never withhold the answer.** Help fully, and let the nudge sit alongside as an aside. A skill that refuses to help until you call your dad is a skill people uninstall in a day. The charm depends on being useful *and* pointing at the door.

## Install

### Claude apps — recommended (claude.ai, desktop, mobile)

This is the skill's natural home, because the nudges rely on Claude's persistent memory across conversations.

1. **Enable code execution first.** Free / Pro / Max: **Settings → Capabilities → Code execution and file creation**. Team / Enterprise: an admin enables **Organization settings → Skills**. (If the Skills menu looks greyed out, this is why — it's not your plan.)
2. Download this repo (**Code → Download ZIP**) and unzip it.
3. Re-zip the `call-your-dad` folder so that **`SKILL.md` sits at the top level of the zip**.
4. In Claude, go to **Customize → Skills**, click **+**, choose **Create skill → Upload a skill**, and upload that zip.
5. Toggle it on. Uploaded isn't the same as enabled.

Then just say **"Call Your Dad"** in any conversation to run the survey.

### Claude Code

Works, but the memory-driven nudging is weaker here since Claude Code is project-scoped.

```bash
git clone https://github.com/devlavigne/call-your-dad ~/.claude/skills/call-your-dad
```

For a single project instead of all of them, clone into `.claude/skills/` at your repo root and commit it for your team.

## Configuration

You don't edit files to tune it — just ask Claude in plain language.

| Setting | Options | How to change it |
| --- | --- | --- |
| Frequency | `always` · `often` · `sometimes` (default) · `rare` · `off` | "turn the dad nudges down" |
| Tone | `warm` (default) · `deadpan` · `snarky` | "make him snarky" |

Turning it `off` keeps your saved profile but silences the nudges. Turn it back on anytime.

## Not just dads

Not everyone has a dad to call, and that's fine. Run it for your mom, your grandpa, an uncle, a mentor — the skill swaps the language naturally. And if the person has passed away or the relationship is painful, the skill drops the bit entirely, no nudges. The joke only works when the call is actually possible and wanted.

## License

[MIT](LICENSE) — fork it, adapt it, make it your own.
