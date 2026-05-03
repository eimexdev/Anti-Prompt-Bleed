# Anti Prompt Bleed

A Codex skill for preventing instruction and prompt bleed in generated website, app, and frontend UI copy.

This skill is narrowly scoped: it removes user-visible leakage of prompts, hidden instructions, implementation requirements, tool/runtime details, planning residue, and agent-process wording. It does not rewrite normal marketing copy, brand voice, slogans, or generic phrasing unless that text exposes internal instructions.

## Install

Install with the skills.sh CLI:

```bash
npx skills add SwiftHustle/Anti-Prompt-Bleed --skill anti-prompt-bleed -a codex -g
```

Then restart Codex so the skill is picked up.

## Use

Invoke it explicitly when reviewing or building frontend work:

```text
Use $anti-prompt-bleed to review this generated website and remove only instruction, prompt, agent, or implementation leakage from visible UI copy.
```

## What It Catches

- Prompt references such as "As requested" or "Based on your request"
- Echoed design or implementation instructions such as "Use lucide icons" or "Keep cards at 8px radius"
- Tool/runtime mentions such as Codex, skills, system prompts, developer messages, commands, or local files
- Planning residue such as TODOs, acceptance criteria, implementation notes, or test plans
- UI copy that describes the generation process instead of the product

## What It Leaves Alone

- Marketing language, even if generic
- Brand voice, slogans, and section labels
- Phrases like "we built", "designed for", or "crafted for" when they read as normal product copy
- Placeholder or mock content unless it leaks task or prompt wording
