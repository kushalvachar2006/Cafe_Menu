# Cafe Menu - Component Development Guide

## Quick Reference for Developers

This guide provides practical examples and patterns for extending and customizing the Cafe Menu components.

---

## Core Components

### 1. Menu Container
**Component:** `.menu`
**Purpose:** Main responsive wrapper

```html
<div class="menu">
    <!-- All menu content goes here -->
</div>
```

**Customization:**
```css
.menu {
    /* Override default styling */
    max-width: 600px;        /* Increase max width */
    background-color: #f4f4f4; /* Change background */
    border-radius: 10px;     /* Add rounded corners */
}
```

---

### 2. Header Component
**Components:** `h1`, `.established`

```html
<!-- Standard Header -->
<h1>CAMPER CAFE</h1>
<p class="established">Est. 2020</p>

<!-- Custom Header Example -->
<h1>YOUR CAFE NAME</h1>
<p class="established">Since 1995</p>
```

---

### 3. Menu Section
**Component:** `section` with items

```html
<!-- Template for new menu section -->
<section>
    <h2>Section Title</h2>
    <img src="icon-url.jpg" alt="section icon" />
    
    <!-- Items go here -->
    <article class="item">
        <p class="flavor">Item Name</p>
        <p class="price">0.00</p>
    </article>
</section>
```

---

### 4. Menu Item Component
**Component:** `.item`

#### Basic Item Structure:
```html
<article class="item">
    <p class="flavor">Item Name</p>
    <p class="price">3.50</p>
</article>
```

#### Item Variants:

**Coffee Item:**
```html
<article class="item">
    <p class="flavor">Espresso</p>
    <p class="price">2.50</p>
</article>
```

**Dessert Item:**
```html
<article class="item">
    <p class="dessert">Chocolate Cake</p>
    <p class="price">4.00</p>
</article>
```

**Custom Item with Description:**
```html
<article class="item">
    <p class="flavor">Premium Blend <span class="description">(Dark Roast)</span></p>
    <p class="price">5.00</p>
</article>
```

---

## Development Patterns

### Adding New Item Types

#### 1. Breakfast Items:
```html
<section>
    <h2>Breakfast</h2>
    <img src="breakfast-icon.jpg" alt="breakfast icon" />
    
    <article class="item">
        <p class="breakfast">Pancakes</p>
        <p class="price">6.50</p>
    </article>
</section>
```

```css
.breakfast {
    text-align: left;
    width: 75%;
    /* Add custom styling for breakfast items */
    color: #8B4513;
}
```

#### 2. Beverages (Non-Coffee):
```html
<section>
    <h2>Beverages</h2>
    <img src="drink-icon.jpg" alt="beverage icon" />
    
    <article class="item">
        <p class="beverage">Fresh Orange Juice</p>
        <p class="price">3.25</p>
    </article>
</section>
```

---

### Layout Modifications

#### Two-Column Layout:
```css
.menu-sections {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
}

.menu-sections section {
    flex: 1;
    min-width: 200px;
}
```

#### Grid Layout for Items:
```css
.section-items {
    display: grid;
    grid-template-columns: 1fr;
    gap: 10px;
}

@media (min-width: 600px) {
    .section-items {
        grid-template-columns: 1fr 1fr;
    }
}
```

---

### JavaScript Integration Examples

#### Dynamic Menu Loading:
```javascript
// Example: Adding items dynamically
function addMenuItem(section, name, price, type = 'flavor') {
    const item = document.createElement('article');
    item.className = 'item';
    
    item.innerHTML = `
        <p class="${type}">${name}</p>
        <p class="price">${price}</p>
    `;
    
    section.appendChild(item);
}

// Usage
const coffeeSection = document.querySelector('section');
addMenuItem(coffeeSection, 'New Blend', '4.75', 'flavor');
```

#### Price Calculator:
```javascript
function calculateTotal() {
    const prices = document.querySelectorAll('.price');
    let total = 0;
    
    prices.forEach(price => {
        total += parseFloat(price.textContent);
    });
    
    return total.toFixed(2);
}
```

---

### Accessibility Enhancements

#### ARIA Labels:
```html
<section role="region" aria-labelledby="coffee-heading">
    <h2 id="coffee-heading">Coffee</h2>
    <!-- items -->
</section>

<article class="item" role="listitem">
    <p class="flavor">French Vanilla</p>
    <p class="price" aria-label="Price: 3 dollars">3.00</p>
</article>
```

#### Keyboard Navigation:
```css
.item:focus-within {
    outline: 2px solid brown;
    outline-offset: 2px;
}
```

---

### Responsive Patterns

#### Mobile-First Approach:
```css
/* Mobile styles (default) */
.menu {
    width: 95%;
    padding: 15px;
}

/* Tablet */
@media (min-width: 768px) {
    .menu {
        width: 85%;
        padding: 20px;
    }
}

/* Desktop */
@media (min-width: 1024px) {
    .menu {
        width: 80%;
        max-width: 500px;
    }
}
```

---

### Theme Customization

#### Dark Theme:
```css
.menu.dark-theme {
    background-color: #2c2c2c;
    color: #f0f0f0;
}

.dark-theme h1,
.dark-theme h2 {
    color: #d4af37;
}

.dark-theme hr {
    background-color: #d4af37;
    border-color: #d4af37;
}

.dark-theme a {
    color: #87ceeb;
}
```

#### Seasonal Themes:
```css
.menu.spring-theme {
    background-color: #f0fff0;
    background-image: linear-gradient(45deg, #f0fff0 25%, #e6ffe6 25%);
}

.menu.autumn-theme {
    background-color: #8b4513;
    color: #ffd700;
}
```

---

### Performance Optimization

#### CSS Optimization:
```css
/* Reduce repaints */
.item p {
    will-change: auto;
    transform: translateZ(0);
}

/* Optimize font loading */
@font-face {
    font-family: 'Impact';
    font-display: swap;
}
```

#### Image Optimization:
```html
<!-- Use modern image formats -->
<picture>
    <source srcset="coffee.webp" type="image/webp">
    <source srcset="coffee.jpg" type="image/jpeg">
    <img src="coffee.jpg" alt="coffee icon" loading="lazy">
</picture>
```

---

## Testing Patterns

### Component Testing:
```javascript
// Example test structure
describe('Menu Item Component', () => {
    test('renders item with name and price', () => {
        const item = createMenuItem('Test Coffee', '3.50');
        expect(item.querySelector('.flavor').textContent).toBe('Test Coffee');
        expect(item.querySelector('.price').textContent).toBe('3.50');
    });
});
```

### Responsive Testing:
```javascript
// Test responsive breakpoints
const breakpoints = [320, 768, 1024, 1200];
breakpoints.forEach(width => {
    test(`layout works at ${width}px`, () => {
        // Test implementation
    });
});
```

---

## Common Customizations

### 1. Adding Item Images:
```html
<article class="item">
    <img src="item-photo.jpg" alt="Item name" class="item-image">
    <div class="item-content">
        <p class="flavor">Item Name</p>
        <p class="price">4.50</p>
    </div>
</article>
```

### 2. Adding Item Descriptions:
```html
<article class="item">
    <div class="item-info">
        <p class="flavor">Specialty Coffee</p>
        <p class="description">Rich blend with chocolate notes</p>
    </div>
    <p class="price">5.25</p>
</article>
```

### 3. Adding Dietary Icons:
```html
<article class="item">
    <p class="flavor">
        Almond Milk Latte 
        <span class="dietary-icons">
            <span class="vegan" title="Vegan">🌱</span>
            <span class="gluten-free" title="Gluten Free">GF</span>
        </span>
    </p>
    <p class="price">4.25</p>
</article>
```

---

## Build and Deploy

### Development Workflow:
1. Edit HTML/CSS directly
2. Test in multiple browsers
3. Validate HTML/CSS
4. Optimize images
5. Deploy to static hosting

### Deployment Checklist:
- [ ] All images optimized
- [ ] CSS minified (optional)
- [ ] HTML validated
- [ ] Cross-browser tested
- [ ] Mobile responsive verified
- [ ] Accessibility checked

---

*Component Guide for Cafe Menu v1.0*