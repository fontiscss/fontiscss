# ⛲ fontis.css – The Algorithmic CSS Framework

> _fontis.css_ **establishes a new generation** of CSS frameworks!

## What does "Algorithmic CSS Framework" mean?

_fontis.css_ is the first CSS framework of its kind. It  does not offer a concrete design, but provides specialized algorithms that promote a harmonious overall appearance. It also offers the option of storing different configurations for an algorithm. This allows you to create a unique design system in no time at all.

> _fontis_ is not like other CSS frameworks. CSS is a programming language and _fontis.css_ activates its power to help you and your team develop unique design systems faster.  
<cite>[David J. Schwarz](https://davidschwarz.eu/) – Creator of fontis.css</cite>

## How it works

_fontis.css_ provides three core algorithms – each covering specific aspects of design:

- `typography`
- `layout`
- `paint`

### How to use the design system

Before you create your first design system with _fontis.css_, take a look at how it will be used afterwards:

```html
<!DOCTYPE html>
<html data-typography data-paint>
<head>
    <style>
        @import url("fontiscss/fontis.css");
        /* Your unique design: */
        @import url("fontiscss/stdlib/layout.css");
        @import url("my-style/extends-fontis.css");
    </style>
</head>
<body>
    <header>...</header>
    <nav>
        <ul data-layout=flex>
            ...
        </ul>
    </nav>
    <main data-typography=pagecontent>
        <article>...</article>
    </main>
    <footer data-paint=pagefooter data-layout=grid-pad>
        <section>...</section>
        <section>...</section>
    </footer>
</body>
```

As you can see, _fontis.css_ uses attributes instead of classes. The attribute marks the element from which the algorithm is applied. **The attribute value refers to the configured variant.** If a descendant element is marked with an algorithm attribute of the same type, the scope ends and the algorithm starts again with the specified configuration.

### How to create your own design system

> To be clear: **It's pure CSS.** You don't need any tools.

Copy or import _fontis.css_ to the beginning of **your CSS file**.

```css
@import url("fontiscss/fontis.css");

/* Your code here. */
```


#### Cascade layers to hook in

_fontis.css_ declares [cascade layers](https://developer.mozilla.org/en-US/docs/Web/CSS/@layer) that you can hook into. For example, each algorithm has a `core` and a `lib` layer. There is also the `bootstrap` layer and the `postprocess` for the finishing touches.

> ℹ️ Tip: _fontis_ has a **standard library** - in case you want to be even faster or looking for some inspiration. More on this in a chapter below.

#### Customize a core algorithm

To customize a base algorithm, **hook into the corresponding `core` layer**. In this example, the typography algorithm is adjusted:

```css
/* my-style/extends-fontis.css */

@layer fontis.typography.core {
    [data-typography] {
        --ft-font-size-base: clamp(1rem, 0.8913rem + 0.5435vw, 1.3125rem);
        --ft-scale-ratio: 1.25;
    }
}
```

#### Create a variant of a core algorithm

To create a variant, add it to the library. To do this, **hook into the corresponding `lib` layer**. To identify the variant, **give it a unique name**. In this example, the name is `pagecontent`.

```css
/* my-style/extends-fontis.css */

@layer fontis.typography.lib {
    [data-typography|="pagecontent"] {
        --ft-font-size-base: calc(1em * var(--FT-SCALE-L));
        --ft-heading-font-family: serif;
        --ft-heading-5-font-family: inherit;
        --ft-heading-6-font-family: inherit;
    }
}
```

#### Standard Library 

The core of _fontis.css_ is reduced to the essentials. This gives you a stable foundation and complete freedom for your ideas. But maybe you want to **skip all the construction work** and concentrate on your outstanding design features. In this case, the standard library offers you **a growing collection of algorithms** that you can easily adopt.

Copy or import the building blocks that fit into your design system idea. For example, a **responsive layout system**:

```css
@import url("fontiscss/fontis.css");

/* Your selection from the Standard Library */
@import url("fontiscss/stdlib/layout.css");

/* Your own code here. */
```

#### 🎉 Congratulations

You have created the basis for **your own design system!**.

## Create something unique

I hope you got an idea how much _fontis.css_ can speed up your design system development and free you to create something unique.

**If you have any questions or feedback**, feel free to open a new [discussion](https://github.com/fontiscss/fontiscss/discussions).

⛲
