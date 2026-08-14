# Editing Guide — Seller Enablement Pages

This guide lets anyone on the team update the two live pages without needing Pavneet. Both are plain HTML files hosted on GitHub Pages — no build step, no framework.

**Live URLs:**
- Sellers page: https://sf-on-sf.github.io/det-ai-enablement-demo/sellers.html
- Feedback form: https://sf-on-sf.github.io/det-ai-enablement-demo/feedback.html

**Repo:** https://github.com/sf-on-sf/det-ai-enablement-demo

---

## How to Make Changes

1. Go to the repo on GitHub
2. Click the file you want to edit (`sellers.html` or `feedback.html`)
3. Click the pencil icon (Edit this file)
4. Make your change (see sections below for what's where)
5. Scroll down, write a short commit message (e.g., "Add new resource link")
6. Click **Commit changes** → select "Commit directly to the `main` branch"
7. Wait 1-2 minutes — GitHub Pages deploys automatically

---

## sellers.html — What's Where

### Left Column: "What You Have Access to Today"

Each resource is a block like this (around lines 90-120):

```html
<a href="URL_HERE" class="res" target="_blank">
  <div class="res-body">
    <div class="res-title">Title shown in bold</div>
    <div class="res-desc">One-line description shown below.</div>
  </div>
</a>
```

**To add a resource:** Copy one of those blocks and paste it before or after an existing one (inside the `<div class="resources">` container). Change the `href`, title, and description.

**To remove a resource:** Delete the entire `<a href="..." class="res">...</a>` block.

**To reorder:** Cut and paste the block to a new position within the list.

---

### Right Column: "At Dreamforce"

Each session category is a block like this (around lines 126-158):

```html
<div class="session-category">
  <div class="cat-header">
    <span class="cat-count">8</span>
    <span class="cat-label">Breakout Sessions</span>
  </div>
  <div class="example">&#8226; Session title here</div>
  <div class="example">&#8226; Another session title</div>
  <a href="URL" class="more-link" target="_blank">See all 8 breakouts &rarr;</a>
</div>
```

**To change session counts:** Edit the number inside `<span class="cat-count">`.

**To change example sessions:** Edit the text after `&#8226;` (that's the bullet character).

**To add/remove example bullets:** Add or delete a `<div class="example">&#8226; Title</div>` line.

**To change the "See all" link:** Edit the `href` in the `<a class="more-link">` tag.

**To add a new category:** Copy an entire `<div class="session-category">...</div>` block and paste it before the "Browse All" button. Pick a border color by changing `border-left-color` in the style attribute:
- Blue: `#0176D3`
- Orange: `#E8772E`
- Purple: `#7C3AED`
- Teal: `#04E1CB`

---

### Hero Section (Top)

Around lines 78-82:

```html
<h1>Your Customer Asks:<br><span>"How Does Salesforce Do It?"</span></h1>
<div class="sub">Resources and sessions to help you answer confidently...</div>
```

Edit the text directly. The `<span>` makes the text blue.

---

### Footer

Line 164 — contains the link to the feedback form and team attribution.

---

## feedback.html — What's Where

### Dropdown: "Your Role" (around lines 40-45)

```html
<select id="role" name="role">
  <option value="">Select...</option>
  <option value="AE">Account Executive</option>
  <option value="SE">Solution Engineer</option>
  <option value="CSM">Customer Success Manager</option>
  <option value="RVP">RVP / Sales Leader</option>
  <option value="Other">Other</option>
</select>
```

**To add a role:** Add a new `<option value="short-code">Display Name</option>` line. The `value` is what gets sent to the backend (keep it short, no spaces).

**To remove a role:** Delete the `<option>` line.

---

### Dropdown: "What kind of feedback?" (around lines 48-55)

```html
<select id="feedback-type" name="feedback_type">
  <option value="">Select...</option>
  <option value="content-request">I need content on a topic not covered</option>
  <option value="improvement">Improvement to existing content</option>
  <option value="other">Other</option>
</select>
```

Same pattern — add or remove `<option>` lines as needed.

---

### Form Labels and Placeholder Text

- Labels are in `<label>` tags — change the text between the tags
- Placeholder text is in `placeholder="..."` attributes on inputs/textareas
- The description below the title is in `<div class="sub">...</div>` (line ~28)

---

### Success Message (after submission)

Around lines 66-68:

```html
<div class="success" id="success">
  <h2>Thanks for your feedback!</h2>
  <p>Your input has been sent to the Customer Zero team...</p>
</div>
```

Edit the text directly.

---

## Things NOT to Touch

| What | Why |
|------|-----|
| The `<script>` block at the bottom of feedback.html | This is the form submission logic — it sends data to a Google Apps Script |
| The Google Apps Script URL in that script | Breaking this breaks form submissions |
| The `<style>` block in either file | This is all the visual styling |
| `class="..."` attributes | These control layout and appearance |
| The `<meta property="og:...">` tags in sellers.html | These control how the link previews in Slack — update them if you change the page title/description |

---

## Quick Reference

| I want to... | File | What to do |
|---|---|---|
| Add a new resource link | sellers.html | Copy a `<a class="res">` block, paste, edit href/title/desc |
| Update session count | sellers.html | Change number in `<span class="cat-count">` |
| Add a feedback type option | feedback.html | Add `<option value="code">Label</option>` in the select |
| Change form description | feedback.html | Edit text in `<div class="sub">` |
| Change success message | feedback.html | Edit text in `<div class="success">` |

---

## Need Help?

- Changes not showing? Wait 2 minutes for GitHub Pages to deploy, then hard-refresh (Ctrl+Shift+R)
- Broke the layout? Use GitHub's file history (click the file → History) to revert to the last working version
- Not sure what to change? Ping Pavneet or ask in #customer-zero-seller-enablement
