# Cafe Menu - Comprehensive API Documentation

## Overview

This documentation covers all public APIs, components, and styling classes for the Cafe Menu project. The project is a responsive static website that displays a cafe menu with coffee and dessert sections.

## Table of Contents

1. [HTML Components](#html-components)
2. [CSS Classes & APIs](#css-classes--apis)
3. [Layout Structure](#layout-structure)
4. [Usage Examples](#usage-examples)
5. [Styling Guide](#styling-guide)
6. [Browser Compatibility](#browser-compatibility)

---

## HTML Components

### Main Container Component

#### `.menu`
The primary container that wraps the entire menu content.

**Structure:**
```html
<div class="menu">
    <!-- Menu content -->
</div>
```

**Properties:**
- Width: 80% of viewport (max 500px)
- Background: Burlywood color
- Auto-centered with padding
- Responsive design

---

### Header Components

#### `h1` - Main Title
**Usage:**
```html
<h1>CAMPER CAFE</h1>
```

**Styling:**
- Font: Impact, serif fallback
- Size: 40px
- Center aligned
- No top margin

#### `.established` - Establishment Date
**Usage:**
```html
<p class="established">Est. 2020</p>
```

**Styling:**
- Italic font style
- Center aligned
- Used for subtitle information

---

### Section Components

#### `section` - Menu Categories
Container for grouping related menu items (Coffee, Desserts, etc.)

**Structure:**
```html
<section>
    <h2>Category Name</h2>
    <img src="category-icon.jpg" alt="category icon" />
    <!-- Menu items -->
</section>
```

#### `h2` - Category Headers
**Usage:**
```html
<h2>Coffee</h2>
<h2>Desserts</h2>
```

**Styling:**
- Font: Impact, serif fallback
- Size: 30px
- Center aligned

---

### Menu Item Components

#### `.item` - Individual Menu Item
Container for each menu item with name and price.

**Structure:**
```html
<article class="item">
    <p class="flavor">Item Name</p>
    <p class="price">Price</p>
</article>
```

**Component Variants:**
- `.flavor` - For coffee items
- `.dessert` - For dessert items

---

### Footer Component

#### `footer` - Contact Information
**Structure:**
```html
<footer>
    <p>
        <a href="https://website.com" target="_blank">Visit our website</a>
    </p>
    <p class="address">123 Address</p>
</footer>
```

---

## CSS Classes & APIs

### Layout Classes

#### `.menu`
**Purpose:** Main container styling
**Properties:**
```css
width: 80%;
background-color: burlywood;
margin: 0 auto;
padding: 20px;
max-width: 500px;
```

#### `.item`
**Purpose:** Menu item container
**Properties:**
```css
/* Inline-block children with specific spacing */
p {
    display: inline-block;
    margin-top: 5px;
    margin-bottom: 5px;
    font-size: 18px;
}
```

---

### Typography Classes

#### `.established`
**Purpose:** Italic subtitle styling
```css
font-style: italic;
```

#### `.flavor` / `.dessert`
**Purpose:** Left-aligned item names
```css
text-align: left;
width: 75%;
```

#### `.price`
**Purpose:** Right-aligned pricing
```css
text-align: right;
width: 20%;
```

#### `.address`
**Purpose:** Footer address styling
```css
margin-bottom: 5px;
```

---

### Separator Classes

#### `hr` (Default)
**Purpose:** Content section dividers
```css
height: 2px;
background-color: brown;
border-color: brown;
```

#### `.bottom-line`
**Purpose:** Footer separator with extra spacing
```css
margin-top: 25px;
```

---

### Link Styling API

#### Link States
```css
a {
    color: black;
}

a:visited {
    color: black;
}

a:hover {
    color: brown;
}

a:active {
    color: brown;
}
```

---

## Layout Structure

### Grid System
The menu uses a flexible layout system:

```
body (background + padding)
└── .menu (centered container)
    ├── main
    │   ├── h1 (title)
    │   ├── .established (subtitle)
    │   ├── hr (divider)
    │   ├── section (coffee)
    │   │   ├── h2
    │   │   ├── img
    │   │   └── .item × n
    │   └── section (desserts)
    │       ├── h2
    │       ├── img
    │       └── .item × n
    ├── hr.bottom-line
    └── footer
```

### Responsive Design
- Container width: 80% (max 500px)
- Images: Auto-centered blocks
- Text: Center-aligned headers
- Items: Flexible inline-block layout

---

## Usage Examples

### Adding a New Menu Item

#### Coffee Item:
```html
<article class="item">
    <p class="flavor">New Coffee Flavor</p>
    <p class="price">5.00</p>
</article>
```

#### Dessert Item:
```html
<article class="item">
    <p class="dessert">New Dessert</p>
    <p class="price">4.25</p>
</article>
```

### Adding a New Menu Section:
```html
<section>
    <h2>New Category</h2>
    <img src="category-icon.jpg" alt="category icon" />
    <article class="item">
        <p class="flavor">Item Name</p>
        <p class="price">Price</p>
    </article>
</section>
```

### Customizing Colors:
```css
/* Override default colors */
.menu {
    background-color: #f5e6d3; /* Custom background */
}

hr {
    background-color: #8B4513; /* Custom divider color */
}

a:hover {
    color: #CD853F; /* Custom link hover color */
}
```

---

## Styling Guide

### Color Palette
- **Primary Background:** `burlywood` (#DEB887)
- **Accent Color:** `brown` (#A52A2A)
- **Text Color:** `black` (#000000)
- **Body Background:** Image-based with beans pattern

### Typography Scale
- **H1:** 40px (Impact font)
- **H2:** 30px (Impact font)
- **Body Text:** 18px (sans-serif)
- **Footer:** 14px (sans-serif)

### Spacing System
- **Container Padding:** 20px
- **Body Padding:** 20px
- **Item Margins:** 5px top/bottom
- **Footer Spacing:** 25px top margin for separator

---

## Browser Compatibility

### Supported Features
- CSS Flexbox (item layout)
- Background images
- Font fallbacks (Impact → serif)
- Pseudo-classes (:hover, :visited, :active)

### Minimum Requirements
- Modern browsers supporting CSS3
- Internet Explorer 11+
- Mobile browsers (responsive design)

### Fallbacks Included
- Font stack: `Impact, serif`
- Generic font family: `sans-serif`

---

## Installation & Setup

### Quick Start
1. Clone/download the project files
2. Ensure all files are in the same directory:
   - `index.html`
   - `style.css`
   - `beans.jpg` (optional - uses CDN fallback)
3. Open `index.html` in a web browser

### File Dependencies
- **Required:** `index.html`, `style.css`
- **Optional:** Local image assets (CDN images used by default)
- **External:** Font families (system fonts with fallbacks)

### Development
No build process required. Direct file editing supported.

### Deployment
Static hosting compatible:
- GitHub Pages
- Netlify
- Vercel
- Any web server

---

## API Reference Summary

| Component | Class | Purpose | Usage |
|-----------|-------|---------|-------|
| Container | `.menu` | Main wrapper | `<div class="menu">` |
| Header | `.established` | Subtitle styling | `<p class="established">` |
| Menu Item | `.item` | Item container | `<article class="item">` |
| Item Name | `.flavor/.dessert` | Left-aligned names | `<p class="flavor">` |
| Price | `.price` | Right-aligned pricing | `<p class="price">` |
| Separator | `.bottom-line` | Footer divider | `<hr class="bottom-line">` |
| Contact | `.address` | Footer address | `<p class="address">` |

---

*Documentation generated for Cafe Menu v1.0*