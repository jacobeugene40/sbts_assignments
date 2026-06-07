# HTML & CSS Assignment - Full Answers

---

## Section A: HTML Basics & Document Structure

---

### Q1. The HTML Skeleton

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Page</title>
  </head>
  <body></body>
</html>
```

| Line | Purpose |
|---|---|
| `<!DOCTYPE html>` | Tells the browser this is an HTML5 document. Without it, browsers enter **quirks mode** — an old compatibility mode that mimics bugs from the 1990s, causing unpredictable layout and styling behaviour. |
| `<html lang="en">` | The root element that wraps all page content. The `lang` attribute declares the page language, which helps screen readers pronounce content correctly and assists search engines. |
| `<head>` | A container for **metadata** — information about the page that isn't displayed directly to the user. |
| `<meta charset="UTF-8">` | Sets the character encoding to UTF-8, allowing the page to correctly display virtually any character from any language (including emojis, accented letters, etc.). Without it, special characters may appear as garbled symbols. |
| `<meta name="viewport" ...>` | Controls how the page scales on mobile devices. `width=device-width` makes the layout width match the screen, and `initial-scale=1.0` prevents auto-zooming. Without this, mobile browsers zoom out and show a tiny desktop view. |
| `<title>My Page</title>` | Sets the text shown in the browser tab and used by search engines as the page headline in results. |
| `<body>` | Contains all visible content — everything the user actually sees in the browser window. |

**What breaks without `<!DOCTYPE html>`?**
The browser switches to quirks mode. This causes:
- The box model to behave differently (e.g. `width` may include padding unexpectedly)
- Certain CSS properties to stop working as expected
- Inconsistent rendering across browsers

---

### Q2. `<head>` vs `<body>`

**Elements that belong in `<head>`** (metadata — not directly rendered):
1. `<title>` — page title shown in browser tab
2. `<meta>` — metadata such as charset, viewport, description, author
3. `<link>` — links to external resources like CSS stylesheets or favicons
4. `<script>` — JavaScript (when loaded before render)
5. `<style>` — internal CSS rules
6. `<base>` — sets the base URL for all relative links

**Elements that belong in `<body>`** (content — directly rendered):
1. `<h1>`–`<h6>` — headings
2. `<p>` — paragraphs
3. `<img>` — images
4. `<a>` — hyperlinks
5. `<form>` — user input forms
6. `<nav>`, `<header>`, `<footer>` — semantic layout sections

**The rule:** If it's *about* the page (metadata, resources, configuration), it goes in `<head>`. If it's *content on* the page (text, images, interactive elements), it goes in `<body>`.

---

### Q3. Block vs Inline Elements

**Block-level elements** start on a new line and stretch to fill the full width of their parent container. They stack vertically.

**Inline elements** flow within the surrounding text and only take up as much width as their content needs. They sit side by side horizontally.

| Type | Examples |
|---|---|
| Block | `<div>`, `<p>`, `<h1>` |
| Inline | `<span>`, `<a>`, `<strong>` |

**Behaviour side by side:**
- Two `<p>` tags placed next to each other in HTML will stack vertically — each on its own line.
- Two `<span>` tags placed next to each other will appear on the same line, flowing like words in a sentence.
- If you place an inline element next to a block element, the block element will still force a new line.

---

### Q4. Attributes Deep Dive

An **HTML attribute** provides additional information or configuration for an element. Attributes are placed inside the opening tag as `name="value"` pairs.

Using `<img>` as the example:

```html
<img src="photo.jpg" alt="A sunset over the sea" width="400" height="300" />
```

| Attribute | Required? | Purpose |
|---|---|---|
| `src` | **Required** | Specifies the image file path. Without it, there is nothing to display — the image is completely broken. |
| `alt` | **Required (for accessibility)** | Provides a text description of the image used by screen readers and shown when the image fails to load. |
| `width` | Optional | Sets the display width in pixels. |
| `height` | Optional | Sets the display height in pixels. |
| `loading` | Optional | E.g. `lazy` — defers loading until the image is near the viewport. |

**What happens if you omit `alt`?**
- Screen readers will either skip the image or read out the filename (e.g. "photo.jpg"), which is meaningless to a visually impaired user.
- The page fails accessibility standards (WCAG).
- Search engines cannot index the image content, harming SEO.
- It is technically invalid HTML.

---

### Q5. Hyperlinks & Paths

**Absolute URL** — the full, complete web address including the protocol and domain. Works from anywhere.

```html
<a href="https://www.bbc.co.uk/news">BBC News</a>
```

**Relative URL** — a path relative to the current file's location. Does not include the domain.

```html
<a href="about.html">About Us</a>
```

**When to use each:**
- Use **absolute URLs** when linking to *external* websites or resources on a different domain.
- Use **relative URLs** when linking to *pages within the same website/project*. They are more portable — if the domain changes, relative links continue to work without any updates.

---

## Section B: Semantic HTML

---

### Q6. What Is Semantic HTML?

**Semantic HTML** means using HTML elements that carry meaning about the content they contain — not just for visual presentation, but to convey structure and purpose to browsers, search engines, and assistive technologies.

**Comparison:**

```html
<!-- Non-semantic -->
<div class="header">
  <p>My Website</p>
</div>

<!-- Semantic -->
<header>
  <h1>My Website</h1>
</header>
```

**Are they visually different by default?** No. Both render as a block-level container with no inherent visual styling.

**Why does it still matter?**
- **Accessibility:** Screen readers use semantic elements to build a navigational outline of the page, allowing users to jump directly to `<main>` or `<nav>`.
- **SEO:** Search engines assign more weight to content in semantic elements like `<article>` and `<h1>`, improving discoverability.
- **Maintainability:** Other developers (and you, six months later) can understand the page structure at a glance without reading `class` names.
- **Browser features:** Some browsers offer reader mode and other features that rely on semantic structure.

---

### Q7. The Sectioning Elements

| Element | Purpose |
|---|---|
| `<header>` | Introductory content for the page or a section — typically contains the logo, site title, and primary navigation. |
| `<nav>` | A block of navigation links — main menus, breadcrumbs, or sidebar navigation. |
| `<main>` | The primary, unique content of the page. There should be only one `<main>` per page. |
| `<section>` | A thematic grouping of related content, typically with its own heading. |
| `<article>` | Self-contained content that could be distributed independently — a blog post, news article, or comment. |
| `<aside>` | Content tangentially related to the surrounding content — sidebars, pull quotes, related links. |
| `<footer>` | Closing content for a page or section — copyright info, secondary links, contact details. |

**ASCII Wireframe:**

```
+------------------------------------------+
|              <header>                    |
|   Logo        <nav> Home | About | Blog  |
+------------------------------------------+
|                                          |
|  <main>                                  |
|  +------------------------------------+  |
|  | <section> Featured Articles        |  |
|  |  +---------------+  +-----------+  |  |
|  |  | <article>     |  | <article> |  |  |
|  |  | Blog Post 1   |  | Blog Post |  |  |
|  |  +---------------+  +-----------+  |  |
|  +------------------------------------+  |
|                                          |
|  <aside> Related Links / Ads            |
+------------------------------------------+
|              <footer>                    |
|   © 2025 My Site | Privacy | Contact     |
+------------------------------------------+
```

---

### Q8. `<section>` vs `<article>` vs `<div>`

| Element | When to use |
|---|---|
| `<article>` | Content that is **self-contained and reusable** — it makes sense on its own even if taken out of context (a blog post, a product card, a forum reply). |
| `<section>` | A **thematic grouping** within a page that needs a heading but isn't independently meaningful on its own (a "Latest Posts" region, a "Our Services" block). |
| `<div>` | A **generic container** with no semantic meaning — use only when no semantic element fits, purely for styling or scripting purposes. |

**Example — Blog Page:**

```html
<main>
  <section>
    <h2>Latest Posts</h2>

    <article>
      <h3>How to Learn CSS in 30 Days</h3>
      <p>CSS can feel overwhelming at first, but with a structured plan...</p>
    </article>

    <article>
      <h3>Top 10 HTML Tips for Beginners</h3>
      <p>Writing clean HTML is a skill that pays dividends for years...</p>
    </article>
  </section>

  <section>
    <h2>About This Blog</h2>
    <div class="author-card">
      <!-- div used here purely as a styling wrapper -->
      <img src="author.jpg" alt="Author photo" />
      <p>Written by Jane Doe, a front-end developer based in London.</p>
    </div>
  </section>
</main>
```

---

### Q9. Headings Hierarchy

**Why skipping heading levels is bad practice:**
- **Accessibility:** Screen readers allow users to navigate by headings. Skipping levels confuses that outline — a user expecting `<h2>` after `<h1>` may miss entire sections.
- **SEO:** Search engines use heading hierarchy to understand page structure and topic relationships. A broken hierarchy weakens indexing quality.
- **Maintainability:** Inconsistent heading levels make the document structure hard to reason about.

**Original (incorrect):**

```html
<h1>My Blog</h1>
  <h4>Latest Posts</h4>
    <h6>Post Title Here</h6>
```

**Corrected:**

```html
<h1>My Blog</h1>
  <h2>Latest Posts</h2>
    <h3>Post Title Here</h3>
```

---

### Q10. Lists — Ordered, Unordered, and Description

| Element | Type | When to use |
|---|---|---|
| `<ul>` | Unordered (bulleted) | Items with no meaningful sequence — a list of features, ingredients, or tags. |
| `<ol>` | Ordered (numbered) | Items where sequence matters — steps in a recipe, a ranking, installation instructions. |
| `<dl>` | Description list | Term–definition pairs — a glossary, a FAQ, or metadata key-value pairs. |

**Real-world examples:**

```html
<!-- Unordered: shopping list (order doesn't matter) -->
<ul>
  <li>Milk</li>
  <li>Eggs</li>
  <li>Bread</li>
</ul>

<!-- Ordered: how to make tea (sequence matters) -->
<ol>
  <li>Boil the kettle</li>
  <li>Place a teabag in the mug</li>
  <li>Pour the boiling water</li>
  <li>Add milk and stir</li>
</ol>

<!-- Description list: glossary -->
<dl>
  <dt>HTML</dt>
  <dd>HyperText Markup Language — the standard language for structuring web pages.</dd>
  <dt>CSS</dt>
  <dd>Cascading Style Sheets — used to style and layout HTML elements.</dd>
</dl>
```

**Why not use lists for visual indentation?**
Lists carry semantic meaning — they tell browsers and screen readers "this is a list of related items." Using them purely for visual indentation misleads assistive technologies (a screen reader may announce "list, 5 items" for content that isn't a list at all), and it produces invalid, confusing HTML. Use CSS `margin` or `padding` for indentation instead.

---

## Section C: HTML Forms

---

### Q11. Anatomy of a Form

The `action` attribute specifies **where** the form data is sent when submitted — typically a URL of a server-side script (e.g. `action="/submit"`). If omitted, data is sent to the current page's URL.

The `method` attribute specifies **how** the data is sent:

| Method | How it works | When to use |
|---|---|---|
| `GET` | Data is appended to the URL as query parameters (e.g. `?name=John&age=25`). Visible in the address bar. Bookmarkable. | Search forms, filters — anything where sharing or bookmarking the result makes sense. |
| `POST` | Data is sent in the HTTP request body, not the URL. Not visible in the address bar. | Login forms, contact forms, payment forms — anything sensitive or that changes server-side data. |

---

### Q12. Input Types

| `type` value | What it does | When to use |
|---|---|---|
| `text` | Single-line free text input | Names, usernames, general short text |
| `email` | Text input with email format validation | Email address fields |
| `password` | Text input that masks characters | Password fields |
| `number` | Numeric input with up/down arrows | Age, quantity, price |
| `tel` | Text input optimised for phone numbers (numeric keyboard on mobile) | Phone number fields |
| `date` | Date picker | Date of birth, appointment booking |
| `checkbox` | Toggleable box — can select multiple | Agreement checkboxes, multi-select options |
| `radio` | One selectable option from a group | Gender, payment method, single-choice options |
| `file` | File upload button | Profile photo upload, document submission |
| `range` | Slider for a numeric value within a range | Volume control, price slider |
| `hidden` | Input not shown to the user | Passing internal data like CSRF tokens or user IDs |
| `submit` | Button that submits the form | Any form submission |

---

### Q13. Labels & Accessibility

Associating a `<label>` with an `<input>` is essential because:
- **Screen readers** announce the label text when the input receives focus, so visually impaired users know what to type.
- **Keyboard users** can click the label text itself to focus the input, increasing the clickable area.
- It is required for valid, accessible HTML (WCAG 2.1 Success Criterion 1.3.1).

**Two correct ways to associate a label:**

**Method 1 — `for` and `id` attributes (explicit association):**
```html
<label for="username">Username</label>
<input type="text" id="username" name="username" />
```

**Method 2 — Wrapping the input inside the label (implicit association):**
```html
<label>
  Username
  <input type="text" name="username" />
</label>
```

**Without a label:**
- Screen readers may read out only the input `type` or `name`, which is often meaningless (e.g. "text field" or "field 3").
- Keyboard users lose the larger click target.
- The form becomes legally non-compliant in many jurisdictions.

---

### Q14. `<select>`, `<textarea>`, and `<button>`

| Element | Purpose |
|---|---|
| `<select>` | A dropdown list from which the user picks one (or multiple) predefined options. |
| `<textarea>` | A multi-line text input area — suitable for longer text like messages or comments. |
| `<button>` | A clickable button. Can submit a form (`type="submit"`), reset it (`type="reset"`), or trigger JavaScript (`type="button"`). |

**Example form snippet:**

```html
<form action="/contact" method="POST">

  <label for="subject">Subject</label>
  <select id="subject" name="subject">
    <option value="">-- Please choose --</option>
    <option value="general">General Enquiry</option>
    <option value="support">Technical Support</option>
    <option value="billing">Billing</option>
  </select>

  <label for="message">Message</label>
  <textarea id="message" name="message" rows="6" placeholder="Write your message here..."></textarea>

  <button type="submit">Send Message</button>
  <button type="reset">Clear Form</button>

</form>
```

---

### Q15. Form Validation Attributes

| Attribute | What it does |
|---|---|
| `required` | The field must not be empty before the form can be submitted. |
| `minlength` | The text input must contain at least this many characters. |
| `maxlength` | The text input cannot exceed this many characters. |
| `min` | For number/date inputs — the value must be at or above this minimum. |
| `max` | For number/date inputs — the value must be at or below this maximum. |
| `pattern` | The value must match a specified regular expression (regex). Useful for postcodes, custom formats, etc. |

**Example using three attributes together:**

```html
<label for="postcode">UK Postcode</label>
<input
  type="text"
  id="postcode"
  name="postcode"
  required
  minlength="5"
  maxlength="8"
  pattern="[A-Z]{1,2}[0-9][0-9A-Z]?\s?[0-9][A-Z]{2}"
  placeholder="e.g. SW1A 1AA"
/>
```

This field: must be filled in (`required`), must be at least 5 characters (`minlength`), no more than 8 (`maxlength`), and must match the UK postcode format (`pattern`).

---

## Section D: CSS Basics & Selectors

---

### Q16. How CSS Connects to HTML

**1. Inline styles** — CSS written directly on an element via the `style` attribute.

```html
<p style="color: red; font-size: 18px;">Hello World</p>
```

- Immediate, no extra files needed
- Highest specificity — very hard to override
- Cannot be reused; mixes concerns (structure + style in one place)
- No pseudo-classes, media queries, or animations possible

**2. Internal `<style>` block** — CSS written inside a `<style>` tag in the `<head>`.

```html
<head>
  <style>
    p { color: red; font-size: 18px; }
  </style>
</head>
```

- Useful for single-page projects or email templates
- No extra HTTP request
- Cannot be shared across multiple pages; each page must repeat the styles

**3. External stylesheet** — CSS written in a separate `.css` file, linked with `<link>`.

```html
<head>
  <link rel="stylesheet" href="styles.css" />
</head>
```

- **Best practice for real projects** — one file styles the entire site
- Browsers cache the CSS file, improving load speed on subsequent pages
- Clear separation of concerns — HTML for structure, CSS for presentation
- Requires an additional HTTP request on first load

**Which to use on a real project?** External stylesheets. They are maintainable, reusable, cacheable, and keep HTML clean.

---

### Q17. CSS Selectors

| Selector | Syntax | Targets |
|---|---|---|
| Element | `p { }` | Every `<p>` element on the page |
| Class | `.card { }` | Every element with `class="card"` |
| ID | `#header { }` | The single element with `id="header"` |

```css
/* Element selector */
p {
  color: black;
}

/* Class selector */
.card {
  color: blue;
}

/* ID selector */
#header {
  color: red;
}
```

**Which rule wins?** If all three target the same element, the **ID selector** wins because it has the highest **specificity**. The order of priority is:

> ID > Class > Element

This concept is called **CSS Specificity**. Each selector has a numerical weight:
- Element selector: **0-0-1**
- Class selector: **0-1-0**
- ID selector: **1-0-0**

Higher numbers win. Inline styles beat all of them (specificity of **1-0-0-0**), and `!important` overrides everything (use sparingly).

---

### Q18. Combinators

**Descendant selector (space)** — selects all matching elements *anywhere* inside the ancestor.

```css
/* Selects every <p> inside a <div>, at any nesting depth */
div p {
  color: grey;
}
```

**Child selector (`>`)** — selects only *direct children* of the parent, not deeper descendants.

```css
/* Selects <p> elements that are direct children of <div> only */
div > p {
  font-weight: bold;
}
```

**Adjacent sibling selector (`+`)** — selects the *immediately following* sibling element.

```css
/* Selects a <p> that comes directly after an <h2> */
h2 + p {
  margin-top: 0;
}
```

**General sibling selector (`~`)** — selects *all* following siblings of the specified type.

```css
/* Selects all <p> elements that are siblings after an <h2> */
h2 ~ p {
  color: dimgray;
}
```

---

### Q19. The Box Model

Every HTML element is a rectangular box made up of four layers, from inside to outside:

```
+------------------------------------------+
|                 MARGIN                   |
|   +----------------------------------+   |
|   |            BORDER                |   |
|   |   +--------------------------+   |   |
|   |   |         PADDING          |   |   |
|   |   |   +------------------+   |   |   |
|   |   |   |     CONTENT      |   |   |   |
|   |   |   +------------------+   |   |   |
|   |   +--------------------------+   |   |
|   +----------------------------------+   |
+------------------------------------------+
```

| Area | Description |
|---|---|
| **Content** | The actual text, image, or child elements |
| **Padding** | Transparent space *inside* the border, between content and border |
| **Border** | A line around the padding and content |
| **Margin** | Transparent space *outside* the border, between this element and others |

**`box-sizing: border-box`**

By default (`content-box`), when you set `width: 300px`, the padding and border are *added on top* of that — so the element is actually wider than 300px. This is counterintuitive.

With `border-box`, the `width` and `height` *include* the padding and border, making layout maths far simpler.

```css
/* Global reset — most developers apply this universally */
*, *::before, *::after {
  box-sizing: border-box;
}
```

---

### Q20. The Cascade & Inheritance

**The Cascade** is the algorithm browsers use to decide which CSS rule applies when multiple rules target the same element. It considers three factors in order:

1. **Origin** — browser default styles < author styles < user styles < `!important`
2. **Specificity** — more specific selectors win (ID > Class > Element)
3. **Source order** — if specificity is equal, the rule declared *later* in the stylesheet wins

**Example:**
```css
p { color: black; }       /* specificity: 0-0-1 */
.intro { color: blue; }   /* specificity: 0-1-0 — wins over element selector */
#hero p { color: red; }   /* specificity: 1-0-1 — wins over class */
```

---

**CSS Inheritance** means some CSS property values set on a parent element are automatically passed down to child elements.

**Properties that ARE inherited by default** (mostly text-related):
- `color`
- `font-family`, `font-size`, `font-weight`
- `line-height`
- `text-align`
- `visibility`

**Properties that are NOT inherited** (mostly box/layout-related):
- `margin`, `padding`
- `border`
- `width`, `height`
- `background`
- `display`, `position`

You can force inheritance using `inherit`:
```css
div { border: 2px solid red; }
p { border: inherit; } /* explicitly inherit the border */
```

---

## Section E: CSS Layout & Responsive Design

---

### Q21. CSS Flexbox — Core Concepts

**Flexbox** (Flexible Box Layout) is a CSS layout model designed to arrange items in a single dimension — either a row or a column — and distribute space between them efficiently.

**The problem it solves:** Before Flexbox, achieving common layouts (like vertically centering an element, or distributing navigation links evenly) required hacky workarounds with floats, tables, or JavaScript. Flexbox makes these trivial.

**Flex container** — the parent element with `display: flex` applied. It controls how its children are laid out.

**Flex items** — the direct children of the flex container. They respond to flex properties.

```css
.container {
  display: flex; /* This makes .container a flex container */
}
/* All direct children of .container are now flex items */
```

**Main axis** — the primary direction along which flex items are laid out. Controlled by `flex-direction`:

| `flex-direction` | Main axis direction | Cross axis direction |
|---|---|---|
| `row` (default) | Left → Right | Top → Bottom |
| `row-reverse` | Right → Left | Top → Bottom |
| `column` | Top → Bottom | Left → Right |
| `column-reverse` | Bottom → Top | Left → Right |

---

### Q22. `justify-content` vs `align-items`

| Property | Controls alignment on... | Default value |
|---|---|---|
| `justify-content` | The **main axis** | `flex-start` |
| `align-items` | The **cross axis** | `stretch` |

With `flex-direction: row`:
- `justify-content` aligns items **horizontally**
- `align-items` aligns items **vertically**

With `flex-direction: column`:
- They **swap** — `justify-content` now controls **vertical** alignment
- `align-items` now controls **horizontal** alignment

**Common values:**
```css
.container {
  display: flex;
  justify-content: space-between; /* spread items across the main axis */
  align-items: center;            /* centre items on the cross axis */
}
```

---

### Q23. Responsive Design Principles

**Responsive web design** is the practice of building websites that adapt their layout and appearance to different screen sizes and devices, providing an optimal viewing experience on everything from a mobile phone to a widescreen desktop.

**Mobile-first approach:** You write your base CSS for small screens first, then use media queries to progressively enhance the layout for larger screens. This is preferred because:
- Mobile is now the dominant browsing context
- It keeps the base CSS lean — smaller files for slower mobile connections
- It forces you to prioritise essential content

**Media query:** A CSS feature that applies rules only when a specified condition (such as screen width) is met.

```css
/* Base styles — mobile first (applies to all screens) */
.container {
  font-size: 14px;
}

/* Media query — applies only when screen is 768px wide or wider */
@media (min-width: 768px) {
  .container {
    font-size: 16px;
  }
}
```

---

### Q24. CSS Units

| Unit | Type | Description | Best use case |
|---|---|---|---|
| `px` | Absolute | Fixed pixels — does not scale with user settings | Borders, shadows, small fixed elements |
| `%` | Relative | Relative to the parent element's size | Fluid widths, responsive images (`width: 100%`) |
| `em` | Relative | Relative to the element's own `font-size` (or nearest parent's) | Padding/margin that should scale with local text size |
| `rem` | Relative | Relative to the **root** (`<html>`) `font-size` | Font sizes across the site — consistent and scalable |
| `vw` | Relative | 1% of the **viewport width** | Full-width hero sections, fluid typography |
| `vh` | Relative | 1% of the **viewport height** | Full-height sections (`height: 100vh`), centring modals |

---

### Q25. Common CSS Layout Patterns with Flexbox

**(a) Horizontal navigation bar with links evenly spaced:**

```css
nav {
  display: flex;
  justify-content: space-evenly; /* or space-between */
  align-items: center;
  background-color: #333;
  padding: 1rem;
}

nav a {
  color: white;
  text-decoration: none;
}
```

**(b) Card grid that wraps on small screens:**

```css
.card-grid {
  display: flex;
  flex-wrap: wrap;        /* allows items to wrap to new rows */
  gap: 1.5rem;
}

.card {
  flex: 1 1 280px;        /* grow, shrink, base width — wraps when space runs out */
  background: #f5f5f5;
  padding: 1.5rem;
  border-radius: 8px;
}
```

**(c) Footer with two columns — one left, one pushed far right:**

```css
footer {
  display: flex;
  justify-content: space-between; /* pushes children to opposite ends */
  align-items: center;
  padding: 1rem 2rem;
}
```

```html
<footer>
  <p>© 2025 My Company</p>
  <nav>
    <a href="/privacy">Privacy</a>
    <a href="/terms">Terms</a>
  </nav>
</footer>
```

---

## Part 2: Practical Assignments

---

## Practical Assignment 1: Personal Profile Page

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Alex Turner — Developer Profile</title>
    <style>
      /* === Reset & Base === */
      *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

      body {
        font-family: Georgia, serif;
        color: #2c2c2c;
        background-color: #fafaf8;
        line-height: 1.7;
      }

      a { color: #1a6fad; text-decoration: none; }
      a:hover { text-decoration: underline; }

      /* === Header === */
      header {
        background-color: #1a1a2e;
        color: #fff;
        padding: 2rem;
        text-align: center;
      }

      header h1 { font-size: 2.5rem; letter-spacing: 0.05em; }
      header p { color: #aab4c8; margin-top: 0.5rem; font-size: 1.1rem; }

      /* === Navigation === */
      nav {
        background-color: #16213e;
        display: flex;
        justify-content: center;
        gap: 2rem;
        padding: 0.75rem;
      }

      nav a {
        color: #e0e0e0;
        font-size: 0.95rem;
        letter-spacing: 0.04em;
        text-transform: uppercase;
      }

      /* === Main Layout === */
      main {
        max-width: 860px;
        margin: 3rem auto;
        padding: 0 1.5rem;
      }

      /* === Bio Section === */
      #bio {
        display: flex;
        gap: 2rem;
        align-items: flex-start;
        margin-bottom: 3rem;
      }

      #bio img {
        width: 160px;
        height: 160px;
        border-radius: 50%;
        object-fit: cover;
        flex-shrink: 0;
        border: 4px solid #1a6fad;
      }

      #bio h2 { font-size: 1.6rem; margin-bottom: 0.75rem; }

      /* === Skills Section === */
      #skills h2 { font-size: 1.6rem; margin-bottom: 1.25rem; }

      .skill-grid {
        display: flex;
        flex-wrap: wrap;
        gap: 0.75rem;
        margin-bottom: 3rem;
      }

      .skill-tag {
        background-color: #1a6fad;
        color: #fff;
        padding: 0.4rem 1rem;
        border-radius: 2rem;
        font-size: 0.9rem;
      }

      /* === Contact Form === */
      #contact h2 { font-size: 1.6rem; margin-bottom: 1.25rem; }

      form { display: flex; flex-direction: column; gap: 1.25rem; }

      label { font-weight: bold; font-size: 0.9rem; display: block; margin-bottom: 0.3rem; }

      input, textarea, select {
        width: 100%;
        padding: 0.75rem 1rem;
        border: 1px solid #ccc;
        border-radius: 6px;
        font-size: 1rem;
        font-family: inherit;
        background-color: #fff;
      }

      input:focus, textarea:focus, select:focus {
        outline: 2px solid #1a6fad;
        border-color: transparent;
      }

      button[type="submit"] {
        background-color: #1a1a2e;
        color: #fff;
        border: none;
        padding: 0.85rem 2rem;
        font-size: 1rem;
        border-radius: 6px;
        cursor: pointer;
        align-self: flex-start;
      }

      button[type="submit"]:hover { background-color: #1a6fad; }

      /* === Footer === */
      footer {
        background-color: #1a1a2e;
        color: #aab4c8;
        text-align: center;
        padding: 1.5rem;
        margin-top: 4rem;
        font-size: 0.9rem;
      }

      /* === Responsive === */
      @media (max-width: 600px) {
        #bio { flex-direction: column; align-items: center; text-align: center; }
        nav { flex-wrap: wrap; gap: 1rem; }
      }
    </style>
  </head>
  <body>

    <header>
      <h1>Alex Turner</h1>
      <p>Front-End Developer &amp; UI Designer based in Manchester, UK</p>
    </header>

    <nav>
      <a href="#bio">About</a>
      <a href="#skills">Skills</a>
      <a href="#contact">Contact</a>
    </nav>

    <main>

      <!-- Bio Section -->
      <section id="bio">
        <img src="https://placehold.co/160x160/1a6fad/ffffff?text=AT" alt="Portrait photo of Alex Turner" />
        <div>
          <h2>About Me</h2>
          <p>
            Hi! I'm Alex, a front-end developer with five years of experience building fast,
            accessible, and visually polished websites. I specialise in HTML, CSS, and JavaScript,
            with a strong interest in design systems and web performance.
          </p>
          <p style="margin-top: 1rem;">
            When I'm not writing code, you'll find me hiking the Peak District, reading sci-fi novels,
            or experimenting with sourdough bread.
          </p>
        </div>
      </section>

      <!-- Skills Section -->
      <section id="skills">
        <h2>Skills</h2>
        <div class="skill-grid">
          <span class="skill-tag">HTML5</span>
          <span class="skill-tag">CSS3</span>
          <span class="skill-tag">JavaScript</span>
          <span class="skill-tag">React</span>
          <span class="skill-tag">Figma</span>
          <span class="skill-tag">Git</span>
          <span class="skill-tag">Accessibility (WCAG)</span>
          <span class="skill-tag">Responsive Design</span>
        </div>
      </section>

      <!-- Contact Form -->
      <section id="contact">
        <h2>Get in Touch</h2>
        <form action="/contact" method="POST" novalidate>

          <div>
            <label for="name">Full Name</label>
            <input
              type="text"
              id="name"
              name="name"
              placeholder="Jane Smith"
              required
              minlength="2"
              maxlength="80"
            />
          </div>

          <div>
            <label for="email">Email Address</label>
            <input
              type="email"
              id="email"
              name="email"
              placeholder="jane@example.com"
              required
            />
          </div>

          <div>
            <label for="reason">Reason for Contact</label>
            <select id="reason" name="reason" required>
              <option value="">-- Please select --</option>
              <option value="work">Work Enquiry</option>
              <option value="collab">Collaboration</option>
              <option value="general">General Question</option>
            </select>
          </div>

          <div>
            <label for="message">Message</label>
            <textarea
              id="message"
              name="message"
              rows="6"
              placeholder="Tell me about your project..."
              required
              minlength="20"
            ></textarea>
          </div>

          <button type="submit">Send Message</button>

        </form>
      </section>

    </main>

    <footer>
      <p>&copy; 2025 Alex Turner. All rights reserved.</p>
    </footer>

  </body>
</html>
```

---

## Practical Assignment 2: Responsive Landing Page

The following is a fully responsive landing page for **BrewBliss** — a fictional specialty coffee shop.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BrewBliss — Specialty Coffee</title>
    <style>
      /* === Reset & Custom Properties === */
      *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

      :root {
        --cream:   #fdf6ec;
        --espresso:#2b1a0e;
        --brown:   #6b3f1e;
        --gold:    #c9913d;
        --light:   #f4ede3;
        --text:    #3a2a1c;
        --muted:   #7a6355;
        --radius:  8px;
      }

      html { scroll-behavior: smooth; }

      body {
        font-family: 'Georgia', serif;
        color: var(--text);
        background-color: var(--cream);
        line-height: 1.75;
      }

      img { max-width: 100%; display: block; }
      a { color: var(--gold); text-decoration: none; }
      a:hover { text-decoration: underline; }

      /* === NAVIGATION === */
      header {
        background-color: var(--espresso);
        position: sticky;
        top: 0;
        z-index: 100;
      }

      nav {
        max-width: 1100px;
        margin: 0 auto;
        padding: 1rem 2rem;
        display: flex;
        justify-content: space-between;
        align-items: center;
      }

      .logo {
        font-size: 1.6rem;
        color: var(--gold);
        letter-spacing: 0.08em;
        font-weight: bold;
      }

      .nav-links {
        display: flex;
        gap: 2rem;
        list-style: none;
      }

      .nav-links a {
        color: #e8d9c8;
        font-size: 0.9rem;
        letter-spacing: 0.05em;
        text-transform: uppercase;
      }

      .nav-links a:hover { color: var(--gold); text-decoration: none; }

      /* === HERO === */
      .hero {
        background-color: var(--espresso);
        color: var(--cream);
        text-align: center;
        padding: 6rem 2rem;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 1.5rem;
      }

      .hero h1 {
        font-size: clamp(2rem, 5vw, 3.5rem);
        color: var(--gold);
        letter-spacing: 0.04em;
      }

      .hero p {
        max-width: 560px;
        font-size: 1.1rem;
        color: #cfc2b3;
      }

      .btn {
        display: inline-block;
        background-color: var(--gold);
        color: var(--espresso);
        padding: 0.85rem 2.5rem;
        border-radius: var(--radius);
        font-size: 1rem;
        font-weight: bold;
        letter-spacing: 0.05em;
        cursor: pointer;
        border: none;
        transition: background-color 0.2s;
      }

      .btn:hover { background-color: #e0a84e; text-decoration: none; }

      /* === SECTION SHARED === */
      section {
        padding: 5rem 2rem;
      }

      .section-inner {
        max-width: 1100px;
        margin: 0 auto;
      }

      .section-title {
        text-align: center;
        font-size: 2rem;
        color: var(--brown);
        margin-bottom: 0.5rem;
      }

      .section-sub {
        text-align: center;
        color: var(--muted);
        margin-bottom: 3rem;
      }

      /* === FEATURES (3 columns) === */
      .features { background-color: var(--light); }

      .feature-grid {
        display: flex;
        flex-wrap: wrap;
        gap: 2rem;
        justify-content: center;
      }

      .feature-card {
        flex: 1 1 260px;
        background: var(--cream);
        border-radius: var(--radius);
        padding: 2rem;
        text-align: center;
        box-shadow: 0 2px 12px rgba(43, 26, 14, 0.08);
      }

      .feature-card .icon {
        font-size: 2.5rem;
        margin-bottom: 1rem;
      }

      .feature-card h3 {
        font-size: 1.2rem;
        color: var(--brown);
        margin-bottom: 0.5rem;
      }

      .feature-card p { color: var(--muted); font-size: 0.95rem; }

      /* === MENU === */
      .menu-grid {
        display: flex;
        flex-wrap: wrap;
        gap: 1.5rem;
      }

      .menu-item {
        flex: 1 1 200px;
        background: var(--light);
        border-radius: var(--radius);
        padding: 1.5rem;
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
        border-left: 4px solid var(--gold);
      }

      .menu-item h3 { color: var(--espresso); font-size: 1.05rem; }
      .menu-item p { color: var(--muted); font-size: 0.9rem; }
      .menu-item .price { color: var(--gold); font-weight: bold; margin-top: auto; }

      /* === ABOUT / TWO COLUMN === */
      .about { background-color: var(--light); }

      .about-inner {
        display: flex;
        flex-wrap: wrap;
        gap: 3rem;
        align-items: center;
        max-width: 1100px;
        margin: 0 auto;
      }

      .about-text { flex: 1 1 300px; }
      .about-text h2 { font-size: 2rem; color: var(--brown); margin-bottom: 1rem; }
      .about-text p { color: var(--muted); margin-bottom: 1rem; }

      .about-img {
        flex: 1 1 300px;
        background: var(--espresso);
        border-radius: var(--radius);
        height: 340px;
        display: flex;
        align-items: center;
        justify-content: center;
        color: var(--gold);
        font-size: 4rem;
      }

      /* === CONTACT FORM === */
      .contact-form {
        max-width: 600px;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        gap: 1.25rem;
      }

      .contact-form label {
        font-size: 0.9rem;
        font-weight: bold;
        color: var(--brown);
        display: block;
        margin-bottom: 0.3rem;
      }

      .contact-form input,
      .contact-form textarea,
      .contact-form select {
        width: 100%;
        padding: 0.75rem 1rem;
        border: 1px solid #d4c4b0;
        border-radius: var(--radius);
        font-family: inherit;
        font-size: 1rem;
        background-color: #fff;
        color: var(--text);
      }

      .contact-form input:focus,
      .contact-form textarea:focus,
      .contact-form select:focus {
        outline: 2px solid var(--gold);
        border-color: transparent;
      }

      .contact-form .btn { align-self: flex-start; }

      /* === FOOTER === */
      footer {
        background-color: var(--espresso);
        color: #cfc2b3;
        padding: 2.5rem 2rem;
      }

      .footer-inner {
        max-width: 1100px;
        margin: 0 auto;
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;
        gap: 1rem;
      }

      .footer-inner .logo { font-size: 1.2rem; }

      .footer-links {
        display: flex;
        gap: 1.5rem;
        list-style: none;
      }

      .footer-links a { color: #cfc2b3; font-size: 0.9rem; }
      .footer-links a:hover { color: var(--gold); }

      /* === RESPONSIVE === */
      @media (max-width: 768px) {
        .nav-links { display: none; } /* In production: replace with hamburger menu */
        .hero { padding: 4rem 1.5rem; }
        .about-img { height: 220px; font-size: 3rem; }
        .footer-inner { flex-direction: column; text-align: center; }
        .footer-links { justify-content: center; }
      }
    </style>
  </head>
  <body>

    <!-- Navigation -->
    <header>
      <nav>
        <span class="logo">BrewBliss</span>
        <ul class="nav-links">
          <li><a href="#features">Why Us</a></li>
          <li><a href="#menu">Menu</a></li>
          <li><a href="#about">Our Story</a></li>
          <li><a href="#contact">Visit Us</a></li>
        </ul>
      </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero">
      <h1>Coffee Worth Waking Up For</h1>
      <p>Single-origin beans, expertly roasted, lovingly brewed. Welcome to BrewBliss — Manchester's finest specialty coffee shop.</p>
      <a href="#menu" class="btn">Explore the Menu</a>
    </section>

    <!-- Features Section -->
    <section class="features" id="features">
      <div class="section-inner">
        <h2 class="section-title">Why BrewBliss?</h2>
        <p class="section-sub">We obsess over every detail so you don't have to.</p>
        <div class="feature-grid">
          <div class="feature-card">
            <div class="icon">☕</div>
            <h3>Single-Origin Beans</h3>
            <p>Sourced directly from small farms in Ethiopia, Colombia, and Guatemala — traceable from crop to cup.</p>
          </div>
          <div class="feature-card">
            <div class="icon">🏆</div>
            <h3>Award-Winning Baristas</h3>
            <p>Our team has competed in the UK Barista Championships. Every espresso is pulled with precision and care.</p>
          </div>
          <div class="feature-card">
            <div class="icon">🌱</div>
            <h3>Sustainably Sourced</h3>
            <p>Fully compostable cups, ethical trade partnerships, and a carbon-neutral roasting process.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Menu Section -->
    <section id="menu">
      <div class="section-inner">
        <h2 class="section-title">Our Menu</h2>
        <p class="section-sub">Simple. Seasonal. Seriously good.</p>
        <div class="menu-grid">
          <div class="menu-item">
            <h3>Espresso</h3>
            <p>A pure, concentrated shot of our signature house blend.</p>
            <span class="price">£2.80</span>
          </div>
          <div class="menu-item">
            <h3>Flat White</h3>
            <p>Velvety microfoam over a double ristretto — the ultimate everyday coffee.</p>
            <span class="price">£3.50</span>
          </div>
          <div class="menu-item">
            <h3>Filter Coffee</h3>
            <p>Slow-brewed V60, showcasing the full flavour profile of our single-origin beans.</p>
            <span class="price">£3.20</span>
          </div>
          <div class="menu-item">
            <h3>Matcha Latte</h3>
            <p>Ceremonial-grade Japanese matcha whisked with steamed oat milk.</p>
            <span class="price">£4.00</span>
          </div>
          <div class="menu-item">
            <h3>Iced Cortado</h3>
            <p>Equal parts espresso and cold milk over ice. Refreshing and bold.</p>
            <span class="price">£3.80</span>
          </div>
          <div class="menu-item">
            <h3>Seasonal Special</h3>
            <p>Ask our baristas — it changes with the season and the harvest.</p>
            <span class="price">From £4.20</span>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section class="about" id="about">
      <div class="about-inner">
        <div class="about-text">
          <h2>Our Story</h2>
          <p>
            BrewBliss began in 2018 when founder Maya Chen returned from a coffee farm visit in Ethiopia with an unshakeable conviction: most people had never tasted coffee at its best.
          </p>
          <p>
            We opened a tiny 12-seat café in the Northern Quarter with three brewing methods and a fierce commitment to quality over quantity. Six years later, we're still that same café — just a little less tiny.
          </p>
          <a href="#contact" class="btn">Find Us</a>
        </div>
        <div class="about-img" role="img" aria-label="Illustration of a coffee cup">
          ☕
        </div>
      </div>
    </section>

    <!-- Contact / Visit Section -->
    <section id="contact">
      <div class="section-inner">
        <h2 class="section-title">Visit or Get in Touch</h2>
        <p class="section-sub">We'd love to hear from you. Drop in or send us a message.</p>
        <form class="contact-form" action="/enquiry" method="POST">

          <div>
            <label for="c-name">Your Name</label>
            <input type="text" id="c-name" name="name" placeholder="Maya Chen" required minlength="2" />
          </div>

          <div>
            <label for="c-email">Email Address</label>
            <input type="email" id="c-email" name="email" placeholder="maya@example.com" required />
          </div>

          <div>
            <label for="c-topic">Topic</label>
            <select id="c-topic" name="topic" required>
              <option value="">-- Select a topic --</option>
              <option value="events">Private Events</option>
              <option value="wholesale">Wholesale Beans</option>
              <option value="feedback">Feedback</option>
              <option value="general">General</option>
            </select>
          </div>

          <div>
            <label for="c-message">Message</label>
            <textarea id="c-message" name="message" rows="5" placeholder="Tell us what's on your mind..." required minlength="10"></textarea>
          </div>

          <button type="submit" class="btn">Send Message</button>

        </form>
      </div>
    </section>

    <!-- Footer -->
    <footer>
      <div class="footer-inner">
        <span class="logo">BrewBliss</span>
        <ul class="footer-links">
          <li><a href="#features">Why Us</a></li>
          <li><a href="#menu">Menu</a></li>
          <li><a href="#about">Our Story</a></li>
          <li><a href="#contact">Contact</a></li>
        </ul>
        <p style="font-size: 0.85rem;">&copy; 2025 BrewBliss Ltd. All rights reserved.</p>
      </div>
    </footer>

  </body>
</html>
```

---

*End of Assignment*