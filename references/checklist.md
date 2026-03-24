# UI/UX "What If" Checklist

Every item is a "what if" question. Run the relevant ones against the code or ticket. If the answer is "not handled" — that's an edge case to flag.

---

## Universal What-Ifs (apply to everything)

### What if the content is too much?
- What if the text is 200+ characters?
- What if a single word is extremely long with no break point? (email, URL)
- What if the text contains emoji? 🎉🔥💀
- What if the text contains line breaks or newlines?
- What if a number is 0? Negative? 999,999,999?
- What if a name has special characters? (O'Brien, Nguyễn, hyphenated, single letter)

### What if the content is too little?
- What if the value is empty string ""?
- What if the value is null or undefined?
- What if there are 0 items in the list?
- What if there is exactly 1 item?
- What if every optional field is missing?

### What if the screen is different?
- What if the user is on a 320px phone?
- What if the user is on a 2560px ultrawide?
- What if the user rotates from portrait to landscape?
- What if the virtual keyboard opens and pushes content up?
- What if there's a notch or safe area (iPhone)?

### What if the user uses keyboard only?
- What if the user presses Tab — where does focus go?
- What if the user presses Escape — does the overlay/dropdown close?
- What if the user presses Enter — does the expected action fire?
- What if the user uses arrow keys — can they navigate options?
- What if focus is invisible — can they tell where they are?

### What if the user is on mobile?
- What if a tap target is smaller than 44×44px?
- What if there's a hover-only interaction? (hover doesn't exist on touch)
- What if scrolling inside a component leaks to the page?
- What if the user swipes and triggers a browser gesture (back swipe on iOS)?

### What if something is loading?
- What if data takes 5 seconds to load — what does the user see?
- What if it takes 30 seconds? (timeout, cancel option?)
- What if the page loads but images are still loading?
- What if content appears and shifts the layout (CLS)?

### What if something fails?
- What if the API returns an error — what does the user see?
- What if the network is offline — is there any feedback?
- What if a retry is needed — is there a retry button?
- What if the error message is vague — does it say WHAT went wrong and HOW to fix?

---

## Dropdown / Select

### What if the list is very long?
- What if there are 50+ options? → Is there a max-height with scroll?
- What if there are 100+ options? → Is there a search/filter?
- What if scrolling inside the dropdown also scrolls the page behind it?

### What if the list is very short?
- What if there are 0 options? → Empty state message?
- What if there is exactly 1 option? → Auto-select it?

### What if option text is very long?
- What if an option label is 60+ characters? → Truncation? Wrapping?
- What if two options have the same display text?

### What if positioning is awkward?
- What if the dropdown trigger is near the bottom of the viewport? → Does it flip upward?
- What if the dropdown is inside a modal or scrollable container? → Does it get clipped?
- What if the dropdown is inside an element with overflow: hidden?

### What if on mobile?
- What if tapping the dropdown on mobile — native select or custom?
- What if the dropdown opens and covers the submit button?

### What if selecting/deselecting?
- What if the user wants to clear their selection? → Is there a reset?
- What if it's multi-select and many items are selected? → How are they displayed? Do tags overflow?
- What if the pre-selected value doesn't exist in the list anymore?
- What if the placeholder text disappears and there's no label?

---

## Text Input / Textarea

### What if the input is extreme?
- What if the user pastes 10,000 characters? → Is there a max-length?
- What if the user pastes rich text (bold, links)? → Does it strip formatting?
- What if there's leading/trailing whitespace? → Is it trimmed?

### What if the user needs help?
- What if the placeholder disappears on focus? → Is there a persistent label?
- What if the format is specific (phone, email)? → Is there helper text?
- What if it's a password field? → Is there a show/hide toggle?
- What if the character limit exists? → Is there a visible counter?

### What if validation is annoying?
- What if the field validates while the user is still typing? (too aggressive)
- What if the field shows error on blur when the user just tabbed through it?
- What if the error message disappears as soon as user starts correcting?
- What if the user can't tell which field has the error?

### What if on mobile?
- What if it's an email field? → Does it show the @ keyboard?
- What if it's a phone field? → Does it show the number keyboard?
- What if it's a number field? → Does it use inputmode="numeric"?
- What if autofill kicks in? → Does it break the layout?

---

## Form (overall)

### What if submitting goes wrong?
- What if the user clicks submit with nothing filled in? → Are all errors shown?
- What if the user clicks submit twice quickly? → Double submission?
- What if the submit button is disabled during loading? → Can user tell why?
- What if the API fails? → Is the form data preserved or lost?
- What if the user navigates away during submit?

### What if the user wants to leave?
- What if the user has unsaved changes and clicks back? → Warning?
- What if the user refreshes the page mid-form? → Data gone?
- What if the browser auto-fills wrong fields?

### What if the form is complex?
- What if field B depends on field A? → Does B update when A changes?
- What if there are required and optional fields? → Is it clear which is which?
- What if there are many errors? → Does the page scroll to the first one?
- What if Tab order doesn't match visual order?

### What if multi-step?
- What if the user clicks back? → Is step data preserved?
- What if the browser back button is pressed? → Previous step or exit?
- What if the user refreshes on step 3? → Data lost?
- What if a step has no content? → What shows?
- What if the progress indicator is missing? → Can user tell where they are?

---

## Table / List / Grid

### What if data is extreme?
- What if there are 0 rows? → Empty state with message?
- What if there is exactly 1 row? → Does the table still look right?
- What if there are 1000+ rows? → Pagination or virtual scroll?
- What if a cell has very long text? → Truncation? Wrapping? Horizontal scroll?

### What if the user interacts?
- What if the user sorts — is the direction visible?
- What if the user filters then sorts — does filter reset pagination?
- What if the user selects rows — is there a select-all? Max selection?
- What if row action buttons overlap content on narrow screens?

### What if on mobile?
- What if the table has 8 columns on a 320px screen? → Horizontal scroll? Card layout?
- What if the header isn't sticky? → User loses context while scrolling.

### What if after filtering?
- What if filters return 0 results? → "No results match" (different from initial empty)
- What if the user clears all filters? → Return to full list?

---

## Modal / Dialog / Drawer

### What if the user wants to close?
- What if the user presses Escape? → Does it close?
- What if the user clicks the backdrop? → Does it close? (careful with forms inside)
- What if the user clicks backdrop while editing? → Data loss warning?
- What if the close button is not visible when content is scrolled?

### What if content overflows?
- What if the modal content is taller than the viewport? → Scrollable?
- What if the user can scroll the page behind the modal? → Body scroll locked?
- What if a modal opens another modal? → Z-index chaos?

### What if focus is wrong?
- What if Tab escapes the modal to background elements? → Focus trap?
- What if the modal closes — where does focus go? → Return to trigger element?

### What if on mobile?
- What if the modal is 600px wide on a 320px screen? → Full-screen?
- What if the keyboard opens inside a modal with form fields?

---

## Button / CTA

- What if the user clicks while loading? → Button disabled + spinner?
- What if the user double-clicks? → Two submissions?
- What if the button text is very long? → Wrapping? Overflow?
- What if it's icon-only? → Is there an aria-label?
- What if the button is for a destructive action? → Different styling? Confirmation?
- What if the button is too small on mobile? → Touch target < 44px?
- What if disabled — can user tell WHY it's disabled?

---

## Search

- What if the user searches with empty string? → What happens?
- What if there are 0 results? → Message + suggestions?
- What if the user types fast? → Debounced? (not firing every keystroke)
- What if the user clears the search? → Easy clear button?
- What if results from a slow old query arrive after a fast new query? → Stale results shown?
- What if the matched text is not highlighted in results?
- What if the query is very long? → Input overflow?

---

## File Upload

- What if the file type is wrong? → Clear rejection message?
- What if the file is too big? → Size limit shown BEFORE upload?
- What if uploading multiple files? → Limit? Individual removal?
- What if an upload fails? → Retry per file?
- What if the user cancels mid-upload? → Cancel button?
- What if it's an image? → Preview/thumbnail shown?
- What if drag-and-drop? → Visual feedback when dragging?
- What if the same file is uploaded twice?

---

## Toast / Notification

- What if a success toast auto-dismisses too fast? → User can't read it?
- What if an error toast auto-dismisses? → User misses the error?
- What if 5 toasts fire at once? → Stacking behavior?
- What if a toast has an action button? → Does it stay long enough?
- What if the toast covers important content?
- What if on screen reader? → Is it announced via aria-live?

---

## Pagination / Infinite Scroll

- What if there are 0 pages? → Hide pagination?
- What if there is 1 page? → Hide pagination?
- What if on the last page? → "Next" disabled?
- What if the page is in the URL? → Bookmarkable? Shareable?
- What if infinite scroll — can the user reach the footer?
- What if the user goes back — is scroll position preserved?

---

## Tabs / Accordion

- What if there is no default tab selected?
- What if the selected tab is not in the URL? → Deep linking broken
- What if there are too many tabs? → Overflow? Scrollable? "More" dropdown?
- What if tab content has very different heights? → Container jumps?
- What if a tab has no content?

---

## Image / Media

- What if the image URL is broken? → Fallback/placeholder?
- What if the image is still loading? → Skeleton?
- What if the image has wrong aspect ratio? → Stretched? Cropped?
- What if there's no alt text? → Accessibility issue
- What if the image is 10MB? → Lazy loading?

---

## Date / Time Picker

- What if the user types an invalid date manually?
- What if past dates should be disabled but aren't?
- What if the date format is wrong for the locale? (DD/MM vs MM/DD)
- What if selecting a range — end before start allowed?
- What if on mobile — native picker or custom?
- What if today is not highlighted?

---

## Navigation / Menu

- What if the current page isn't indicated in the nav?
- What if the menu has 3+ nesting levels? → Usable?
- What if on mobile — hamburger or bottom nav?
- What if the mobile menu doesn't close after clicking a link?
- What if there are too many menu items? → Overflow?

---

## Card / Tile

- What if the title overflows? → Truncation?
- What if cards in a grid have different heights? → Uneven layout?
- What if the whole card is clickable vs just some parts? → Click target confusion?
- What if the image is missing? → Layout breaks or fallback?
- What if optional fields (subtitle, badge, tags) are all missing?

---

## OTP / Verification Input

- What if the user pastes the full OTP? → Does it fill all fields?
- What if backspace is pressed? → Goes to previous digit?
- What if SMS auto-fill on mobile? → autocomplete="one-time-code"?
- What if the OTP expires? → Timer shown?
- What if the user wants to resend? → Cooldown timer?
- What if wrong OTP? → Attempts remaining shown?
- What if max attempts exceeded? → Lockout message?
- What if the keyboard on mobile isn't numeric?

---

## Stepper / Multi-step Flow

- What if the user clicks back? → Step data preserved?
- What if browser back button? → Goes to previous step, not exit?
- What if user refreshes on step 3? → Data lost?
- What if user wants to edit a completed step? → Can jump back?
- What if there's no progress indicator?
- What if the last step has no review/summary before submit?

---

## CRUD Edge Cases (Create / Read / Update / Delete)

### Creating
- What if the same thing is submitted twice? → Duplicate prevention?
- What if creation succeeds but user doesn't see confirmation?
- What if creation fails — is the form data still there?

### Reading
- What if the data was deleted by someone else while viewing?
- What if the data is stale — when was it last refreshed?

### Updating
- What if the user hasn't changed anything and clicks save?
- What if there's no "unsaved changes" indicator?
- What if the form is pre-filled with wrong current values?

### Deleting
- What if there's no confirmation dialog?
- What if the confirmation says "Are you sure?" without saying WHAT is being deleted?
- What if delete fails — item still showing?
- What if there's no undo option?
- What if deleting cascades (also deletes child items) — is user warned?

---

## Quick-Fire What-Ifs (run through these for any component)

1. What if there are **0 items**?
2. What if there are **1000 items**?
3. What if the text is **200 characters long**?
4. What if the text is **empty**?
5. What if the user **double-clicks**?
6. What if the user is on a **320px screen**?
7. What if the user uses **only keyboard**?
8. What if the **API returns an error**?
9. What if the user **refreshes mid-action**?
10. What if the value is **null or undefined**?
11. What if the user **pastes instead of typing**?
12. What if there are **emoji or special characters**?
13. What if the user **navigates back**?
14. What if this is the user's **first time** seeing this screen?
15. What if the **loading takes 10 seconds**?
16. What if the user is on **iOS Safari**?
17. What if every optional field is **missing**?
18. What if the user **resizes the window** mid-interaction?

---

## Severity Guide

**🔴 Critical** — Breaks layout, makes feature unusable, loses user data, blocks the main flow

**🟡 Should-have** — Poor but functional, missing loading/error/empty state, not working on mobile, not keyboard-accessible

**🟢 Nice-to-have** — Polish, affects < 1% users, animation smoothness, micro-copy improvement
