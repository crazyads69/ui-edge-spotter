# 🔍 UI Edge Spotter

Spot uncovered UI/UX edge cases by asking "what if" questions.

An agent skill that reviews your component code or ticket description and surfaces the visual/interaction gaps you missed. **Does not generate code** — outputs a structured audit for the dev to evaluate.

## Install

### skills.sh (all agents)

```bash
npx skills add crazyads69/ui-edge-spotter
```

### Claude Code

```bash
# Project-local
npx skills add crazyads69/ui-edge-spotter

# Global (all projects)
npx skills add crazyads69/ui-edge-spotter --global
```

### Cursor / Windsurf / Codex CLI

```bash
npx add-skill crazyads69/ui-edge-spotter
```

### Claude.ai (web / mobile)

1. Download `ui-edge-spotter.skill` from [Releases](../../releases)
2. Go to **Customize → Skills**
3. Click **+** → **Upload a skill**

### Manual

```bash
git clone https://github.com/crazyads69/ui-edge-spotter.git
cp -r ui-edge-spotter ~/.claude/skills/ui-edge-spotter
```

## Usage

Paste code and ask **"spot edge cases"**, **"what could break"**, or **"what did I forget"**.

```
Here's my phone number dropdown. What edge cases am I missing?

<SelectPhone numbers={phoneList} onChange={handleSelect} />
```

Output:
```
🔍 What-If Audit: Phone Number Dropdown

⚠️ What if user has 50+ phone numbers?
Currently: Dropdown grows forever, pushes submit off-screen
Impact: 🔴 Critical
Suggest: Max-height ~10 items with scroll

⚠️ What if user has 0 phone numbers?
Currently: Not handled — blank dropdown
Impact: 🟡 Should-have
Suggest: Empty state with "Add a number" CTA

⚠️ What if dropdown opens near viewport bottom?
Currently: Gets cut off
Impact: 🟡 Should-have
Suggest: Flip upward when no space below

📊 Summary: 🔴 1 · 🟡 3 · 🟢 1
```

## What It Covers

**22 component types**: dropdown, input, form, table, modal, button, search, file upload, toast, pagination, tabs, image, date picker, navigation, card, OTP, stepper, tooltip, toggle, skeleton, badge, and data mutations (create/update/delete).

**7 universal categories**: content overflow, content absence, responsive screens, keyboard navigation, mobile touch, loading states, failure states.

**10-item quick-fire audit** for a 30-second speed run on any component.

## Structure

```
ui-edge-spotter/
├── SKILL.md              ← Skill instructions + output format
├── references/
│   └── checklist.md      ← "What if" questions by component type
├── README.md
└── LICENSE
```

## Compatibility

Works with any agent supporting the SKILL.md open standard:

Claude Code · Cursor · Windsurf · Codex CLI · Cline · Roo Code · Aide · OpenCode · Augment · Claude.ai (via .skill upload)

## License

MIT
