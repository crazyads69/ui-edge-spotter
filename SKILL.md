---
name: ui-edge-spotter
description: >
  Spot uncovered UI/UX edge cases in frontend code or ticket descriptions by asking "what if" questions 
  about layout, states, content, and interactions. Outputs issues the dev can evaluate — does NOT generate code.
  Use when: reviewing UI component code (dropdown, form, modal, table, input, search, stepper, OTP), 
  checking tickets for missing edge cases, doing frontend code review, or when someone asks 
  "what UI issues am I missing", "spot edge cases", "review this component", "what could break", 
  "what did I forget", "UI audit", or "what edge cases". 
  Also triggers when user pastes React/Vue/HTML/CSS code for any interactive component and asks for review.
  Covers: layout overflow, empty/loading/error states, text overflow, responsive, touch targets, 
  dropdown positioning, form validation, keyboard navigation, and component-specific edge cases.
license: MIT
metadata:
  author: crazyads69
  version: "1.0.0"
  tags: ["ui", "ux", "edge-cases", "frontend", "code-review", "react", "what-if", "accessibility", "mobile"]
---

# UI Edge Spotter

Spot uncovered UI/UX edge cases by thinking in "what if" questions.

## How It Works

1. Read `references/checklist.md` — it contains "what if" questions organized by component type
2. Identify the component(s) in the user's code or ticket
3. Run the relevant "what if" questions against what's implemented
4. Output only the gaps — things NOT handled

## Output Format

```
### 🔍 What-If Audit: [Component Name]

**Context**: [What was analyzed]

---

#### ⚠️ What if [scenario]?
**Currently**: [What happens now — or "not handled"]
**Impact**: 🔴 Critical / 🟡 Should-have / 🟢 Nice-to-have
**Suggest**: [Brief direction, no code]

---

#### ✅ Already handled
- [Things done well]

#### 📊 Summary
🔴 N critical · 🟡 N should-have · 🟢 N nice-to-have
```

## Rules

- **DO NOT generate code.** Only describe the issue.
- **Be specific.** "What if user has 50+ phone numbers? → dropdown pushes submit off-screen" — not "consider long lists."
- **5-8 focused issues.** Not 30 theoretical ones.
- **Give credit** for what IS handled.
- **The dev decides** what to fix. Frame as questions, not demands.

## Example

Input: "Phone number dropdown, no height limit"

Output:
```
🔍 What-If Audit: Phone Number Dropdown

⚠️ What if user has 50+ phone numbers?
Currently: Dropdown grows forever, pushes page content off-screen
Impact: 🔴 Critical
Suggest: Max-height ~10 items with scroll

⚠️ What if user has 0 phone numbers?
Currently: Not handled — empty dropdown or nothing shows
Impact: 🟡 Should-have
Suggest: Empty state "No numbers yet"

⚠️ What if phone label is very long? (+84 123 456 789 — Số công ty)
Currently: Text overflows dropdown width
Impact: 🟢 Nice-to-have
Suggest: Truncate with ellipsis, tooltip on hover
```
