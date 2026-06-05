# CSS Theory Assignment

## Q1. What is CSS and how do you add it to an HTML page?

### What is CSS?

CSS stands for **Cascading Style Sheets**. It is used to control the appearance and layout of web pages. HTML provides the structure of a webpage, while CSS makes it visually attractive by adding colors, spacing, fonts, animations, and responsive layouts.

### What problem does CSS solve?

Without CSS, websites would look plain and difficult to use. CSS separates design from content, making websites easier to maintain and update.

### Three Ways to Add CSS

#### 1. Inline CSS

Applied directly inside an HTML element using the `style` attribute.

```html
<h1 style="color: blue;">Hello World</h1>
```

#### 2. Internal CSS

Written inside a `<style>` tag within the HTML document.

```html
<head>
  <style>
    h1 {
      color: blue;
    }
  </style>
</head>
```

#### 3. External CSS

Written in a separate `.css` file and linked to HTML.

**index.html**

```html
<head>
  <link rel="stylesheet" href="styles.css">
</head>
```

**styles.css**

```css
h1 {
  color: blue;
}
```

### Which method is recommended?

External CSS is recommended because:

* Keeps HTML clean
* Reusable across multiple pages
* Easier maintenance
* Better performance through browser caching

---

# Q2. Explain CSS Selectors with Examples

CSS selectors are used to target HTML elements and apply styles.

## 1. Element Selector

```css
p {
  color: blue;
}
```

## 2. Class Selector

```css
.card {
  border: 1px solid black;
}
```

## 3. ID Selector

```css
#header {
  background-color: black;
}
```

## 4. Group Selector

```css
h1,
h2,
h3 {
  color: navy;
}
```

## 5. Descendant Selector

Targets any nested element.

```css
div p {
  color: green;
}
```

## 6. Child Selector

Targets direct children only.

```css
div > p {
  color: red;
}
```

## 7. Universal Selector

Targets every element.

```css
* {
  margin: 0;
  padding: 0;
}
```

### Class vs ID

| Class                        | ID                      |
| ---------------------------- | ----------------------- |
| Reusable                     | Unique                  |
| Can be used on many elements | Should only appear once |
| Specificity: 10              | Specificity: 100        |

### Answers

* Higher specificity: **ID**
* Direct child: `>`
* Any descendant: space (` `)
* Same class on multiple elements: **Yes**
* Same ID on multiple elements: **No**

### Code Task

```css
/* Universal */
* {
  box-sizing: border-box;
}

/* Element */
p {
  color: blue;
}

/* Class */
.card {
  padding: 10px;
}

/* ID */
#hero {
  background: black;
}

/* Group */
h1,
h2,
h3 {
  font-family: Arial;
}

/* Descendant */
.container p {
  color: green;
}

/* Child */
.container > p {
  font-weight: bold;
}
```

---

# Q3. What is the CSS Box Model?

Every HTML element is treated as a rectangular box.

### 1. Content

The actual text, image, or content inside the element.

### 2. Padding

Space between content and border.

### 3. Border

Wraps around padding and content.

### 4. Margin

Space outside the border.

### Order

```text
Margin
 └ Border
    └ Padding
       └ Content
```

### Answers

* Innermost layer: **Content**
* Padding is **inside** the border
* `margin: 0 auto` centers a block element horizontally
* In `border-box`, width includes padding and border

### Content Box vs Border Box

#### content-box (default)

```css
width: 300px;
```

Total width becomes:

```text
300 + padding + border
```

#### border-box

```css
box-sizing: border-box;
```

Width remains exactly 300px including padding and border.

Professional projects commonly use:

```css
box-sizing: border-box;
```

### Code Task

```css
.box {
  width: 300px;
  padding: 20px;
  border: 2px solid black;
  margin: 16px;
  box-sizing: border-box;
}
```

---

# Q4. Explain CSS Colors

CSS provides multiple ways to define colors.

## 1. Named Color

```css
color: orange;
```

## 2. HEX

```css
color: #f97316;
```

## 3. RGB

```css
color: rgb(249, 115, 22);
```

## 4. RGBA

```css
color: rgba(249, 115, 22, 1);
```

## 5. HSL

```css
color: hsl(25, 95%, 53%);
```

### Answers

* Most common format: **HEX**
* A in RGBA = **Alpha (transparency)**
* Opacity affects child elements: **Yes**
* RGBA affects child elements: **No**

### Opacity vs RGBA

```css
opacity: 0.5;
```

Makes the entire element and children transparent.

```css
background: rgba(0, 0, 0, 0.5);
```

Only the color becomes transparent.

### Same Orange Color in All Formats

```css
color: orange;

color: #f97316;

color: rgb(249, 115, 22);

color: rgba(249, 115, 22, 1);

color: hsl(25, 95%, 53%);
```

---

# Q5. What are CSS Units?

## px

Fixed pixels.

```css
font-size: 16px;
```

## %

Relative to parent element.

```css
width: 50%;
```

## rem

Relative to root (`html`) font size.

```css
font-size: 2rem;
```

Default:

```text
1rem = 16px
```

## em

Relative to parent font size.

```css
padding: 1.5em;
```

## vh

Viewport height.

```css
height: 100vh;
```

## vw

Viewport width.

```css
width: 100vw;
```

### Answers

* 1rem = 16px by default
* % is relative to parent
* vh = viewport height
* rem improves accessibility because users can scale text

### Golden Rule

* Font sizes → rem
* Widths → %, flex, grid
* Full screen sections → vh

### Code Task

```css
.hero {
  height: 100vh;
  max-width: 75rem;
  margin: auto;
  font-size: clamp(1rem, 2vw, 2rem);

  display: flex;
  justify-content: center;
  align-items: center;
}
```

---

# Q6. What is CSS Specificity and how does the Cascade work?

Specificity determines which CSS rule wins when multiple rules target the same element.

## Specificity Scores

| Selector     | Score |
| ------------ | ----- |
| Inline Style | 1000  |
| ID           | 100   |
| Class        | 10    |
| Element      | 1     |

### Cascade Rules

1. Importance (`!important`)
2. Specificity
3. Source Order
4. Inheritance

### Answers

* Higher specificity: Class > Element
* Inline style score: 1000
* Equal specificity: Last rule wins
* `!important` overrides normal specificity

### Why avoid `!important`?

It makes debugging difficult and breaks predictable styling.

### Code Task

HTML

```html
<p id="intro" class="text">Hello</p>
```

CSS

```css
p {
  color: blue;
}

.text {
  color: green;
}

#intro {
  color: red;
}
```

Winner:

```css
#intro {
  color: red;
}
```

Because ID specificity (100) is higher than class (10) and element (1).

---

# Q7. Explain CSS Flexbox

Flexbox is a one-dimensional layout system used to align items in rows or columns.

```css
display: flex;
```

turns an element into a flex container.

## flex-direction

```css
flex-direction: row;
```

```css
flex-direction: column;
```

## justify-content

Controls alignment on the main axis.

```css
justify-content: center;
```

## align-items

Controls alignment on the cross axis.

```css
align-items: center;
```

## flex-wrap

```css
flex-wrap: wrap;
```

Allows items to move onto new lines.

## gap

```css
gap: 20px;
```

Creates spacing between items.

## flex: 1

```css
flex: 1;
```

Makes items grow equally.

### Real World Uses

1. Navigation bars
2. Card layouts

### Centering with Flexbox

```css
display: flex;
justify-content: center;
align-items: center;
```

### Code Task

```css
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
}

.nav-links {
  display: flex;
  gap: 1rem;
}
```

---

# Q8. What are CSS Pseudo-classes and Pseudo-elements?

### Pseudo-class

Changes style based on state.

Uses single colon:

```css
:hover
```

### Pseudo-element

Creates virtual content.

Uses double colon:

```css
::before
```

## Pseudo-classes

### :hover

```css
button:hover {
  background: orange;
}
```

### :focus

```css
input:focus {
  border-color: blue;
}
```

### :nth-child()

```css
li:nth-child(2n) {
  background: lightgray;
}
```

Selects every even element.

### :not()

```css
p:not(.active) {
  color: gray;
}
```

## Pseudo-elements

### ::before

```css
.featured::before {
  content: "★ ";
}
```

### ::after

```css
.btn::after {
  content: " →";
}
```

### ::placeholder

```css
input::placeholder {
  color: gray;
}
```

### Answers

* ::before does not create a real HTML element
* Required property: `content`
* `:nth-child(2n)` selects even elements
* Every 3rd item:

```css
li:nth-child(3n) {
  color: orange;
}
```

### Code Task

```css
button:hover {
  background-color: #f97316;
}

.featured::before {
  content: "★ ";
  color: orange;
}

input::placeholder {
  color: gray;
}
```

---

# Q9. Explain CSS Transitions and Animations

## Transition

Used when a property changes from one state to another.

```css
transition: property duration timing-function delay;
```

Example:

```css
transition: transform 0.3s ease;
```

### Timing Functions

```css
ease
ease-in
ease-out
linear
```

## Animation

Runs automatically using keyframes.

```css
@keyframes fadeIn {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}
```

### Animation Shorthand

```css
animation: fadeIn 1s ease forwards;
```

### animation-fill-mode: forwards

Keeps the final animation state after completion.

### Answers

* Common triggers: hover, focus, active
* Multiple transitions: Yes
* `animation-iteration-count: infinite` repeats forever
* Transform is faster because it uses GPU acceleration and avoids layout recalculations

### Code Task

```css
.card {
  padding: 2rem;
  border-radius: 12px;
  background: white;

  transition: transform 0.3s ease,
              box-shadow 0.3s ease;

  animation: fadeUp 0.8s ease forwards;
}

.card:hover {
  transform: translateY(-10px);

  box-shadow: 0 10px 20px rgba(0,0,0,0.2);
}

@keyframes fadeUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}
```

---

# Q10. What is Responsive Web Design? Explain Media Queries, CSS Variables, and Mobile-First Approach

Responsive Web Design (RWD) ensures websites look good on all devices.

## Part A – Media Queries

### Syntax

```css
@media (min-width: 768px) {

}
```

### Common Breakpoints

| Device  | Width   |
| ------- | ------- |
| Mobile  | 0–767px |
| Tablet  | 768px   |
| Laptop  | 1024px  |
| Desktop | 1280px+ |

---

## Part B – Mobile First

Mobile-first means designing for small screens first and then enhancing for larger screens.

### Why Industry Standard?

* Better performance
* Better accessibility
* Easier scaling

### Mobile First Uses

```css
min-width
```

### Desktop First Uses

```css
max-width
```

---

## Part C – CSS Variables

Variables store reusable values.

### Define Variables

```css
:root {
  --primary: #f97316;
}
```

### Use Variables

```css
button {
  background: var(--primary);
}
```

### Fallback Value

```css
color: var(--text-color, black);
```

If variable doesn't exist, black is used.

### Dark Mode

```css
@media (prefers-color-scheme: dark) {

}
```

Detects user system dark mode preference.

### Can JavaScript Change CSS Variables?

Yes.

```javascript
document.documentElement.style.setProperty(
  "--primary",
  "#000"
);
```

### Code Task

```css
/* Design System */

:root {
  --primary: #f97316;
  --background: #ffffff;
  --text: #111111;

  --font-base: 1rem;

  --space-sm: 0.5rem;
  --space-md: 1rem;
  --space-lg: 2rem;
}

/* Base */

body {
  background: var(--background);
  color: var(--text);
  font-size: var(--font-base);
}

/* Dark Theme */

[data-theme="dark"] {
  --background: #111111;
  --text: #ffffff;
}

/* System Dark Mode */

@media (prefers-color-scheme: dark) {
  body {
    background: var(--background);
    color: var(--text);
  }
}

/* Tablet */

@media (min-width: 768px) {
  body {
    font-size: 1.1rem;
  }
}

/* Desktop */

@media (min-width: 1024px) {
  body {
    font-size: 1.2rem;
  }
}
```

---

# Conclusion

CSS is the styling language of the web. It provides powerful tools such as selectors, the box model, colors, units, Flexbox, pseudo-classes, animations, responsive design, media queries, and CSS variables. Understanding these concepts helps developers create modern, responsive, and professional websites.
