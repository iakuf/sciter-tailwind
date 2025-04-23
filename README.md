# Sciter Tailwind: Tailwind-Inspired Utility Mixins for Sciter.js

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A lightweight utility-first CSS library inspired by [Tailwind CSS](https://tailwindcss.com/), specifically designed for [Sciter.js](https://sciter.com/). It leverages Sciter's powerful `@mixin` feature to provide reusable styling components directly within your CSS or inline styles.

## Why Sciter Tailwind?

- **Tailwind Philosophy in Sciter:** Brings the utility-first approach of Tailwind CSS to the Sciter.js environment. Apply styles directly where you need them without constantly switching context to CSS files.
- **Leverages Sciter's Power:** Utilizes Sciter's native `@mixin` functionality for efficient and reusable styles.
- **Lightweight & Dependency-Free:** Optimized for Sciter.js with no external dependencies.
- **Intuitive & Familiar:** Offers an API similar to Tailwind CSS, making it easy to pick up if you're familiar with Tailwind.
- **Customizable:** Easily extend or modify the library by adjusting variables and adding your own mixins in `sciter-tailwind.css`.

## Installation

1.  Download the `sciter-tailwind.css` file.
2.  Place it in your Sciter.js project directory.
3.  Link it in the `<head>` section of your HTML file:

    ```html
    <head>
      <meta charset="utf-8">
      <title>My Sciter App</title>
      <!-- Link the CSS file -->
      <link rel="stylesheet" href="sciter-tailwind.css">
      <style>
        /* Optional: Define global styles or component styles here */
        body {
          @bg-color(@gray-100); /* Apply background using a mixin */
        }
      </style>
    </head>
    ```

## Usage

Unlike traditional Tailwind which uses utility classes in HTML, Sciter Tailwind uses `@mixin` syntax. You can apply these mixins either within `<style>` tags or directly in the `style` attribute of HTML elements.

**1. In CSS (`<style>` tag or separate `.css` file):**

```css
/* Define styles for a container element */
.my-container {
  @flex-col;         /* Apply vertical flex layout */
  @items-center;     /* Center items vertically */
  @p(10px);          /* Apply 10px padding on all sides */
  @bg-color(@gray-100); /* Set background color using a predefined variable */
  @rounded(5px);     /* Apply 5px border radius */
}

/* Define styles for a button */
.my-button {
  @btn(@blue-600, white); /* Use the predefined button mixin */
  @mb(8px);               /* Apply 8px margin-bottom */
  @shadow-md;             /* Apply medium box shadow */
}
```

**2. Inline in HTML (`style` attribute):**

This is often preferred for applying utility styles directly to elements, similar to the Tailwind CSS class approach.

```html
<body>
  <div style="@flex-col; @items-center; @p(16px); @bg-color(white); @rounded(8px); @shadow-lg;">
    <h1 style="@text-2xl; @font-bold; @text-color(@gray-800); @mb(10px);">Welcome!</h1>
    <p style="@text-color(@gray-600); @mb(15px);">This is styled using inline Sciter Tailwind mixins.</p>
    <button style="@btn(@green-500, white); @px(12px); @py(6px);">Click Me</button>
  </div>

  <!-- Another example -->
  <div style="@flex-row; @justify-between; @items-center; @p(8px); @bg-color(@blue-100); @mt(20px);">
    <span>Item 1</span>
    <span>Item 2</span>
  </div>
</body>
```

## Available Utility Mixins

Here's a list of the core mixins provided. Refer to `sciter-tailwind.css` for the exact implementation and available variables (like colors and sizes).

*(Note: `size` parameters usually accept standard CSS units like `px`, `em`, `%`, etc. `color` parameters usually accept color names, hex codes, or predefined color variables like `@blue-500`)*

### Layout
*   `@flex`: Basic flex display.
*   `@flex-row`: Horizontal flow (`flow: horizontal`).
*   `@flex-col`: Vertical flow (`flow: vertical`).
*   `@flex-wrap`: Wrapping horizontal flow (`flow: horizontal-wrap`).
*   `@items-start`, `@items-center`, `@items-end`: Vertical alignment.
*   `@justify-start`, `@justify-center`, `@justify-end`, `@justify-between`: Horizontal alignment/distribution.
*   `@grid`: Basic grid flow (`flow: grid`).
*   `@grid-template-columns(columns)`: Define grid columns (e.g., `1fr 1fr`).
*   `@grid-gap(gap)`: Set spacing between grid items.

### Spacing (Margin & Padding)
*   `@m(size)`, `@mx(size)`, `@my(size)`, `@mt(size)`, `@mr(size)`, `@mb(size)`, `@ml(size)`: Margin utilities.
*   `@p(size)`, `@px(size)`, `@py(size)`, `@pt(size)`, `@pr(size)`, `@pb(size)`, `@pl(size)`: Padding utilities.

### Sizing
*   `@w(size)`, `@h(size)`: Width and Height.
*   `@min-w(size)`, `@min-h(size)`: Minimum Width/Height.
*   `@max-w(size)`, `@max-h(size)`: Maximum Width/Height.
*   `@w-full`, `@h-full`: 100% Width/Height.

### Typography
*   `@text(size)`: Font size (e.g., `@text(1.2em)`).
*   `@text-sm`, `@text-base`, `@text-lg`, `@text-xl`, `@text-2xl`, `@text-3xl`, `@text-4xl`: Predefined font sizes based on variables.
*   `@font-bold`, `@font-normal`: Font weight.
*   `@text-left`, `@text-center`, `@text-right`: Text alignment.
*   `@text-color(color)`: Text color.
*   `@truncate`: Prevent text wrapping and add ellipsis (`overflow-x: hidden; text-overflow: ellipsis; white-space: nowrap;`).

### Backgrounds & Borders
*   `@bg-color(color)`: Background color.
*   `@rounded(size)`: Border radius.
*   `@rounded-full`: Fully rounded corners (`border-radius: 9999px`).
*   `@border(width, color)`: Set border (e.g., `@border(1px, @gray-300)`).

### Effects
*   `@shadow-sm`, `@shadow`, `@shadow-md`, `@shadow-lg`: Box shadows of varying sizes.

### Components (Predefined Styles)
*   `@btn(bg-color, text-color)`: Basic button styling.
*   `@card`: (Currently not defined in the provided CSS, but listed in the old README - consider adding or removing).

## Example

Check out the `tailwind-test.htm` file for a comprehensive demonstration of various mixins in action.

## Customization

Feel free to modify `sciter-tailwind.css`:

-   **Colors:** Adjust the `@const` color variables (e.g., `@blue-500`) to match your brand palette.
-   **Spacing/Sizing:** Modify default spacing or sizing values if needed.
-   **Mixins:** Add new mixins for your specific UI patterns or extend existing ones.

## Important Notes

-   This library is **specifically for Sciter.js** and will not work in standard web browsers due to its reliance on Sciter-specific CSS features (`@mixin`, `flow`, etc.).
-   Styling is applied via `@mixin` calls, not HTML classes.
-   Parameterized mixins (e.g., `@p(size)`) offer flexibility.

## Contributing

Contributions, issues, and feature requests are welcome!

## License

[MIT](https://opensource.org/licenses/MIT)