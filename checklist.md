# UI/UX "What If" Checklist

Every item is a "what if" question. If the answer is "not handled" — flag it.

**How to use**: Check SKILL.md Step 1 to find which sections apply, then run only those sections. Don't check everything for every component.

---

## Universal (apply to every component)

### Content overflow
- What if the text is 200+ characters? → Truncated? Ellipsis? Tooltip for full text?
- What if a single word has no break point? (long email address, URL) → word-break applied?
- What if the text contains emoji? 🎉🔥 → Renders correctly? Doesn't break line height?
- What if the text contains newlines? → Rendered or collapsed?
- What if a number is 0? Negative? 999,999,999? → Formatted with separators?
- What if a name has special characters? (O'Brien, Nguyễn, hyphenated, single-letter)

### Content absence
- What if the value is empty string ""?
- What if the value is null or undefined?
- What if there are 0 items in the list? → Empty state shown?
- What if there is exactly 1 item? → Layout still correct?
- What if every optional field is missing? → Layout doesn't collapse?

### Different screens
- What if the user is on a 320px phone? → Nothing overflows or overlaps?
- What if the user is on a 2560px ultrawide? → Content not awkwardly stretched?
- What if the user rotates from portrait to landscape?
- What if the virtual keyboard opens? → Active input still visible?
- What if there's a notch or safe area? (iPhone, Galaxy cutout)

### Keyboard
- What if the user presses Tab? → Focus moves in logical order?
- What if the user presses Escape? → Overlay/dropdown closes?
- What if the user presses Enter? → Expected action fires?
- What if the user uses arrow keys? → Can navigate options?
- What if focus ring is invisible? → `outline: none` without replacement?

### Mobile touch
- What if a tap target is smaller than 44×44px?
- What if there's a hover-only interaction? (no hover on touch devices)
- What if scrolling inside a component leaks to the page behind it?
- What if the user swipes and triggers browser back gesture? (iOS Safari)

### Loading
- What if data takes 3+ seconds to load? → What does the user see?
- What if it takes 30 seconds? → Timeout? Cancel option?
- What if the page loads but images haven't loaded yet? → Layout shift (CLS)?

### Failure
- What if the API returns an error? → User sees a clear message?
- What if the network is offline? → Any feedback at all?
- What if a retry is needed? → Retry button available?
- What if the error message is vague? → Says WHAT went wrong and HOW to fix?

---

## Dropdown / Select

### Long list
- What if there are 50+ options? → Max-height with scroll?
- What if there are 100+ options? → Search/filter input?
- What if scrolling inside the dropdown also scrolls the page?

### Short list
- What if there are 0 options? → Empty state message?
- What if there is exactly 1 option? → Auto-select?

### Long option text
- What if an option label is 60+ characters? → Truncation or wrapping?
- What if two options have the same display text?

### Positioning
- What if the trigger is near the bottom of the viewport? → Flips upward?
- What if the dropdown is inside a scrollable container or modal? → Clipped?
- What if a parent has overflow: hidden? → Dropdown cut off?

### Mobile
- What if tapping on mobile? → Native select or custom bottom sheet?
- What if the dropdown opens and covers the submit button?

### Selection state
- What if the user wants to clear their selection? → Reset/clear button?
- What if multi-select and many items selected? → Tags overflow? Count shown?
- What if the pre-selected value no longer exists in the list?
- What if the placeholder disappears and there's no persistent label?

---

## Text Input / Textarea

### Extreme input
- What if the user pastes 10,000 characters? → Max-length enforced?
- What if the user pastes rich text (bold, links)? → Stripped to plain text?
- What if there's leading/trailing whitespace? → Trimmed on submit?

### User guidance
- What if the placeholder disappears on focus? → Persistent label above?
- What if the format is specific (phone, email)? → Helper text visible?
- What if it's a password field? → Show/hide toggle?
- What if there's a character limit? → Visible counter?

### Validation timing
- What if the field validates while the user is still typing? (too aggressive)
- What if the field shows error on blur when the user just tabbed through without typing?
- What if the error message disappears immediately when user starts correcting?
- What if the user can't tell which field has the error? → Inline error + highlight?

### Mobile keyboard
- What if it's an email field? → Keyboard shows @?
- What if it's a phone field? → Number pad?
- What if it's a numeric field? → inputmode="numeric"?
- What if autofill kicks in? → Breaks layout or styling?

---

## Form (overall)

### Submission
- What if the user clicks submit with nothing filled in? → All errors shown at once?
- What if the user clicks submit twice quickly? → Double submission prevented?
- What if the submit button is disabled during loading? → Spinner shown? User knows why?
- What if the API fails on submit? → Form data preserved, not wiped?
- What if the user navigates away during an in-progress submit?

### Leaving the form
- What if the user has unsaved changes and clicks back? → Warning dialog?
- What if the user refreshes the page mid-form? → Data gone?
- What if browser autofill populates wrong fields?

### Complex forms
- What if field B depends on field A? → B updates when A changes?
- What if required and optional fields aren't labeled? → User can tell which is which?
- What if there are many errors? → Page scrolls to first error?
- What if Tab order doesn't match visual layout?

---

## Stepper / Multi-step Flow

- What if the user clicks the back button inside the stepper? → Step data preserved?
- What if the browser back button is pressed? → Goes to previous step, not exits the flow?
- What if the user refreshes mid-flow? → Data lost or persisted?
- What if the user wants to edit a completed step? → Can jump back?
- What if there's no progress indicator? → "Step 2 of 5"?
- What if the last step has no review/summary before final submit?

---

## Table / List / Grid

### Data extremes
- What if there are 0 rows? → Empty state with message (not blank)?
- What if there is exactly 1 row? → Table still looks correct?
- What if there are 1000+ rows? → Pagination or virtual scroll?
- What if a cell has very long text? → Truncation? Tooltip? Horizontal scroll?

### Interaction
- What if the user sorts? → Current sort direction visually indicated?
- What if the user filters then sorts? → Filter resets pagination to page 1?
- What if the user selects rows? → Select-all? Max selection limit?
- What if row action buttons overlap content on narrow screens?

### Mobile
- What if the table has 8 columns on a 320px screen? → Horizontal scroll? Card layout?
- What if the header isn't sticky? → User loses column context while scrolling

### After filtering
- What if filters return 0 results? → "No results match" message (different from empty state)?
- What if the user clears all filters? → Returns to full list?

---

## Modal / Dialog / Drawer

### Closing
- What if the user presses Escape? → Closes?
- What if the user clicks the backdrop? → Closes? (careful — data loss if form inside)
- What if the user clicks backdrop while editing inside? → Warning first?
- What if the close button is not visible when content is scrolled down?

### Overflow
- What if the modal content is taller than the viewport? → Modal body scrollable?
- What if the user can scroll the page behind the modal? → Body scroll locked?
- What if a modal opens another modal? → Z-index correct? Focus managed?

### Focus
- What if Tab key escapes the modal to background? → Focus trapped inside?
- What if the modal closes? → Focus returns to the element that opened it?

### Mobile
- What if the modal is 600px wide on a 320px screen? → Full-screen on mobile?
- What if the keyboard opens inside a modal with form inputs? → Input still visible?

---

## Button / CTA

- What if the user clicks while an async action is in progress? → Disabled + spinner?
- What if the user double-clicks? → Two submissions?
- What if the button text is very long? → Wrapping or overflow?
- What if it's icon-only? → aria-label for screen readers?
- What if it's a destructive action (delete)? → Red styling? Confirmation step?
- What if the button is too small on mobile? → Touch target < 44px?
- What if the button is disabled? → Can user tell WHY? (tooltip or hint)

---

## Search

- What if the user searches with empty string? → What happens?
- What if there are 0 results? → "No results" message + suggestions?
- What if the user types fast? → Debounced (not firing every keystroke)?
- What if the user wants to clear? → Clear button visible?
- What if a slow old query's results arrive after a newer query? → Stale results displayed?
- What if matched text is not highlighted in results?
- What if the query text is very long? → Input overflows?

---

## File Upload

- What if the file type is wrong? → Clear rejection message?
- What if the file is too big? → Size limit shown BEFORE upload attempt?
- What if uploading multiple files? → Max count? Remove individual files?
- What if an upload fails? → Retry button per file?
- What if the user wants to cancel mid-upload? → Cancel button?
- What if it's an image? → Preview/thumbnail?
- What if drag-and-drop? → Visual feedback when dragging over drop zone?
- What if the same file is uploaded twice? → Warning or silent accept?

---

## Toast / Notification

- What if a success toast auto-dismisses too fast? → User can't read it?
- What if an error toast auto-dismisses? → User misses the error? (errors should persist)
- What if 5 toasts fire at once? → Stacking? Queue?
- What if a toast has an action button? → Stays long enough to click?
- What if the toast covers important content or input fields?
- What if a screen reader user can't hear it? → aria-live region?

---

## Pagination / Infinite Scroll

- What if there are 0 pages? → Pagination hidden?
- What if there is 1 page? → Pagination hidden?
- What if on the last page? → "Next" button disabled?
- What if the current page is in the URL? → Bookmarkable? Shareable?
- What if infinite scroll? → Can the user ever reach the footer?
- What if the user navigates back? → Scroll position preserved?

---

## Tabs / Accordion

- What if there is no default tab selected? → First tab auto-selected?
- What if the selected tab is not reflected in the URL? → Deep linking broken
- What if there are too many tabs for the viewport width? → Scrollable? "More" dropdown?
- What if tab panels have very different content heights? → Container jumps on switch?
- What if a tab panel has no content? → Empty state shown?

---

## Image / Media

- What if the image URL is broken? → Fallback placeholder shown?
- What if the image is still loading? → Skeleton or blur placeholder?
- What if the image aspect ratio is wrong? → Stretched? Cropped? (object-fit)
- What if there's no alt text? → Screen reader announces nothing useful
- What if the image file is 10MB? → Lazy loaded? Compressed variant?

---

## Date / Time Picker

- What if the user types an invalid date manually? → Validation + clear error?
- What if past dates should be disabled but aren't?
- What if the date format is wrong for the user's locale? (DD/MM vs MM/DD)
- What if selecting a date range? → End before start prevented?
- What if on mobile? → Native date picker or custom?
- What if today's date is not visually highlighted?

---

## Navigation / Menu

- What if the current page isn't indicated in the nav? → No active state?
- What if the menu has 3+ nesting levels? → Still usable?
- What if on mobile? → Hamburger or bottom nav?
- What if the mobile menu doesn't close after clicking a link?
- What if there are too many menu items for the viewport? → Overflow handling?

---

## Card / Tile

- What if the title overflows? → Truncation with ellipsis?
- What if cards in a grid have different content heights? → Uneven rows?
- What if the whole card is clickable vs just specific elements? → Click target clear?
- What if the card image is missing? → Layout breaks or fallback?
- What if all optional fields (subtitle, badge, tags) are missing? → Card still looks intentional?

---

## OTP / Verification Input

- What if the user pastes the full OTP from clipboard? → Auto-fills all fields?
- What if backspace is pressed? → Moves to previous digit and clears?
- What if SMS auto-fill on mobile? → autocomplete="one-time-code" set?
- What if the OTP expires? → Countdown timer visible?
- What if the user wants to resend? → Resend button with cooldown?
- What if wrong OTP entered? → Attempts remaining shown?
- What if max attempts exceeded? → Lockout message?
- What if mobile keyboard isn't numeric? → inputmode="numeric" set?

---

## Tooltip / Popover

- What if the trigger is near the viewport edge? → Tooltip repositions (flips)?
- What if the tooltip content is very long? → Max-width with wrapping?
- What if on mobile? → Tooltip shows on tap, not hover? Dismissible?
- What if the tooltip covers the content the user is trying to read?
- What if the user needs to interact with tooltip content (links, copy text)? → Stays open?
- What if keyboard users trigger the tooltip? → Shows on focus, not just hover?

---

## Toggle / Switch / Checkbox

- What if the toggle label doesn't clearly state what each position means? → "On" / "Off" ambiguous?
- What if the toggle triggers an immediate action vs saving on submit? → User expects which?
- What if the toggle is saving (async)? → Loading state on the toggle?
- What if the save fails? → Toggle reverts to previous position?
- What if there's an indeterminate state? (parent checkbox with mixed children)
- What if the click target is just the toggle track? → Label should also be clickable

---

## Skeleton / Loading Placeholder

- What if the skeleton dimensions don't match the real content? → Layout shift when loaded
- What if the skeleton is shown for < 200ms? → Flash/flicker? (add minimum display time)
- What if loading fails? → Skeleton stays forever? Or transitions to error state?
- What if the skeleton looks too similar to real content? → User tries to interact with it?

---

## Badge / Tag / Chip

- What if there are 20+ tags? → Overflow handling? "+N more" indicator?
- What if a tag text is very long? → Max-width with truncation?
- What if tags are removable? → Remove button has adequate touch target?
- What if all tags are removed? → Empty state?
- What if a tag wraps to the next line? → Layout still aligned?

---

## Data Mutations (create / update / delete)

Only check this section if the component creates, updates, or deletes data.

### After creating
- What if the same thing is submitted twice? → Duplicate prevented?
- What if creation succeeds? → User sees clear confirmation?
- What if creation fails? → Form data still present, not wiped?
- What if the created item should appear in a list? → Visible immediately or after refresh?

### After updating
- What if the user clicks save without changing anything? → No-op or unnecessary API call?
- What if there's no visual indicator that changes are unsaved? → Dirty state shown?
- What if the form loads with stale or wrong current values?

### After deleting
- What if there's no confirmation dialog? → Accidental deletion?
- What if the confirmation is generic "Are you sure?" → Should name WHAT is being deleted
- What if delete fails? → Item still visible, error shown?
- What if there's no undo? → Destructive and irreversible
- What if deleting cascades (removes child items too)? → User warned?

---

## Quick-fire audit (30-second speed run)

Use this list when you want a fast pass on ANY component without reading the full sections above. Each question is a yes/no — if "no", dig deeper in the relevant section.

1. **Zero state** — What does it look like with no data?
2. **Overflow** — What if there's way more content than expected?
3. **Empty text** — What if a text value is missing or blank?
4. **Small screen** — Does it work at 320px?
5. **Double action** — What if the user clicks/submits twice?
6. **Keyboard** — Can a keyboard-only user operate it?
7. **Error** — What does the user see when something fails?
8. **Loading** — What does the user see while waiting?
9. **First visit** — Would a new user understand what to do?
10. **iOS Safari** — Does it behave the same as Chrome?
