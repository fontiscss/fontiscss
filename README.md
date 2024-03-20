# ⛲ fontis.css – The Algorithmic CSS Framework

> _fontis.css_ **establishes a new generation** of CSS frameworks!

## What does "Algorithmic CSS Framework" mean?

_fontis.css_ is the first CSS framework of its kind. It  _does not_ offer a concrete design, but provides specialized algorithms that promote a harmonious overall appearance. It also offers the option of storing different configurations for an algorithm. This allows you to create a unique design system in no time at all.

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
<body data-typography data-paint>
    <header>...</header>
    <nav>
        <ul data-layout="flex">
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

As you can see, _fontis.css_ uses **attributes instead of classes**. The attribute marks the element from which the algorithm is applied. The attribute value refers to the configured variant. If a descendant element is marked with an algorithm attribute of the same type, the scope ends and the algorithm starts again with the specified configuration.

### How to create your own design system

> To be clear: **It's pure CSS.** You don't need any tools.

Copy or import _fontis.css_ to the beginning of **your CSS file**.

```css
@import url("path/to/fontis.css");

/* Your code here. */
```

#### cascade layers to hook in

_fontis.css_ declares cascade layers that you can hook into. Each algorithm has a `core` and a `lib` layer.

#### customize a core algorithm

To customize a base algorithm, **hook into the corresponding `core` layer**. In this example, the typography algorithm is adjusted:

```css
/* ... */

@layer fontis.typography.core {
    [data-typography] {
        --ft-font-size-base: clamp(1rem, 0.8913rem + 0.5435vw, 1.3125rem);
        --ft-scale-ratio: 1.25;
    }
}
```

#### create a variant of a core algorithm

To create a variant, add it to the library. To do this, **hook into the corresponding `lib` layer**. To identify the variant, **give it a unique name**. In this example, the name is `pagecontent`.

```css
@layer fontis.typography.lib {
    [data-typography|="pagecontent"] {
        --ft-font-size-base: calc(1em * var(--FT-SCALE-L));
        --ft-heading-font-family: serif;
        --ft-heading-5-font-family: inherit;
        --ft-heading-6-font-family: inherit;
    }
}
```

#### 🎉 Congratulations

You have created the basis for **your own design system!**.

## Create something unique

I hope you got an idea how much _fontis.css_ can speed up your design system development and free you to create something unique.

**If you have any questions or feedback**, feel free to open a new [discussion](https://github.com/fontiscss/fontiscss/discussions).

⛲
