---
name: anti-prompt-bleed
description: Prevent instruction and prompt bleed in generated website, app, and frontend UI copy. Use when an AI coding agent designs, builds, edits, or reviews websites, landing pages, dashboards, SaaS apps, product interfaces, React/Vue/Svelte/HTML screens, seed content, mock data, onboarding flows, forms, empty states, errors, or any user-visible web/app text that could accidentally expose hidden instructions, user prompts, implementation requirements, design constraints, tool behavior, system/developer guidance, planning notes, or internal task wording.
---

# Anti Prompt Bleed

Prevent internal instructions from becoming user-visible website or app copy. First understand what the application is about, then decide whether a word is leaked instruction text or normal product terminology. Do not rewrite copy for taste, marketing quality, brand voice, genericness, or style unless the text contains instruction bleed.

## Scope

Only remove or rewrite text that leaks instructions, prompts, process constraints, or implementation details into the visible product.

Allowed:
- Marketing language, even if generic.
- Phrases like "we built", "designed for", or "crafted for" when they read as normal product copy.
- Brand voice, slogans, section labels, and sales copy unless they expose internal instructions.
- Placeholder or mock content unless it includes leaked prompt/task language.
- Domain terms that belong to the product, including words like "prompt", "model", "assistant", "workflow", "agent", "system", "developer", or "generation" when the app is actually about AI, automation, developer tools, writing tools, or prompt management.

Not allowed:
- Text that reveals what the assistant was told to do.
- Text that reveals system, developer, skill, or user instructions.
- Text that reveals implementation requirements not meant for users.
- Text that describes the generation process instead of the product.

## What Instruction Bleed Looks Like

Treat these as defects when they appear in user-visible UI:

- Prompt references: "Based on your request", "As requested", "This page was generated", "The prompt asked for".
- Instruction echoes: "Use lucide icons", "Make the first screen the app", "Avoid gradient orbs", "Keep cards at 8px radius", "Use AIDA".
- Assistant/process text: "I created", "I implemented", "Here is", "This component includes", "The layout uses".
- Requirements as copy: "Responsive on mobile and desktop", "Accessible with semantic HTML", "Built with React and Tailwind" unless the product is explicitly selling those facts to users.
- Internal constraints: "No placeholder text", "No generic AI aesthetics", "No explanatory copy", "Follow the design system".
- Planning residue: "Step 1", "TODO", "Acceptance criteria", "Success criteria", "Implementation notes", "Test plan".
- Tool/runtime leakage: mentions of model behavior, system prompts, developer messages, skills, tools, local files, commands, or generated assets.
- Hidden-context contamination: text that uses wording from private instructions rather than from the product domain.

## Context Gate

Before changing any suspicious term, classify the app domain and ask whether the term is product-native.

Keep terms when they are part of the product experience:

- AI/prompt tools: "prompt library", "prompt history", "system prompt", "model settings", "assistant response", "generate", "run prompt".
- Developer tools: "build", "deploy", "component", "test", "schema", "API", "logs".
- Automation tools: "workflow", "agent", "trigger", "action", "run", "execution".
- Writing tools: "draft", "rewrite", "generate", "tone", "instructions".

Only flag those terms when they point back to the creation of the website/app itself or to hidden instructions. For example, "Prompt library" is valid in a prompt-management app. "This page was generated from your prompt" is bleed unless that sentence is a deliberate feature of the product.

## Workflow

1. Identify the app domain, audience, and product vocabulary from the user's request and the existing UI.
2. Identify instruction sources: user request, system/developer constraints, skill guidance, implementation plan, TODOs, comments, and framework/tool choices.
3. Inspect every user-visible string in the built surface: HTML/JSX/templates, constants, seed data, mock data, metadata, alt text, aria labels, errors, loading states, and empty states.
4. Compare visible strings against both the product vocabulary and the instruction sources. Flag only text that repeats, paraphrases, or reveals instructions rather than serving the product.
5. Rewrite the smallest possible span. Preserve the surrounding marketing style, voice, layout, and product message.
6. If a phrase is merely generic, cheesy, or uses an instruction-adjacent word in a valid product context, leave it alone.

## Rewrite Rules

- Convert leaked instructions into product-facing meaning only when there is a real user need.
- Delete leaked text when it has no user-facing purpose.
- Keep the original tone when editing around a leak.
- Do not introduce new claims, features, metrics, or brand positioning while fixing bleed.
- Do not use the cleanup as a reason to redesign copy.

Examples:

| Leaky visible text | Minimal fix |
| --- | --- |
| "Built with responsive cards and lucide icons for a clean dashboard." | "Your dashboard" or remove the sentence |
| "As requested, the app opens directly to the editor." | "Editor" |
| "This section follows the AIDA framework with strong CTAs." | Replace with actual section copy or remove |
| "No gradient orbs, no generic AI aesthetics." | Remove |
| "Use the filters below to test the React state." | "Filter results" |
| "Generated sample testimonial for social proof." | Remove or replace only if real testimonial copy was supplied |
| "Save this prompt to your library." | Keep in an AI/prompt app |
| "System prompt" | Keep when it names a real product field |
| "Prompt generated from the user request: build a SaaS landing page." | Remove the leaked request wording |

## Final Check

Before delivery, verify:

- No visible text references prompts, instructions, assistants, tools, skills, implementation, tests, TODOs, or design constraints unless those terms are legitimate product vocabulary.
- No hidden/system/developer/user instruction wording appears as page copy.
- No implementation requirement is exposed unless the product intentionally talks about that technology.
- Product-native terms are preserved in AI, developer, writing, and automation tools.
- Non-leaky marketing copy is preserved, even if it is not how you would personally write it.
- Fixes are minimal and targeted to instruction bleed only.
