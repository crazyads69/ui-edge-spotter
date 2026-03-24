# 🔍 UI Edge Spotter

Spot uncovered UI/UX edge cases by asking "what if" questions.

A skill that acts as a senior UI/UX reviewer — runs "what if" questions against your component code or ticket description and surfaces the gaps. **Does not generate code** — outputs issues for the dev to evaluate.

## Install

```bash
# skills.sh (all agents)
npx skills add crazyads69/ui-edge-spotter

# Or manually
git clone https://github.com/crazyads69/ui-edge-spotter.git
cp -r ui-edge-spotter/skills/ui-edge-spotter ~/.claude/skills/
```

Works with Claude Code, Cursor, Windsurf, Codex CLI, Cline, Roo Code, Aide, OpenCode, Augment.

## Usage

Paste code and ask **"spot edge cases"**, **"what could break"**, or **"what did I forget"**.

```
Here's my phone number dropdown. What if edge cases?

<SelectPhone numbers={phoneList} onChange={handleSelect} />
```

Output:
```
🔍 What-If Audit: Phone Number Dropdown

⚠️ What if user has 50+ phone numbers?
Currently: Dropdown grows forever, pushes submit off-screen
Impact: 🔴 Critical

⚠️ What if user has 0 phone numbers?
Currently: Not handled
Impact: 🟡 Should-have

📊 Summary: 🔴 1 · 🟡 3 · 🟢 2
```

## What It Covers

**18 "what if" question sets** for: dropdown, input, form, table, modal, button, search, file upload, toast, pagination, tabs, image, date picker, navigation, card, OTP, stepper, CRUD operations.

**Universal what-ifs**: content too much/too little, different screen sizes, keyboard-only, mobile touch, loading states, error states.

**18 quick-fire what-ifs** you can run against any component in 30 seconds.

## Philosophy

5-8 focused issues that matter. Not 30 theoretical ones.

## License

MIT
