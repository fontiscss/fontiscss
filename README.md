# keen.css – The Algorithmic CSS Framework

> _keen.css_ **establishes a new generation** of CSS frameworks!

## What does "Algorithmic CSS Framework" mean?

_keen.css_ is the first CSS framework of its kind. It  does not offer a concrete design, but provides specialized algorithms that promote a harmonious overall appearance. It also offers the option of storing different configurations for an algorithm. This allows you to create a unique design system in no time at all.

> _keen_ is not like other CSS frameworks. CSS is a programming language and _keen.css_ activates its power to help you and your team develop unique design systems faster.  
<cite>[David J. Schwarz](https://davidschwarz.eu/) – Creator of keen.css</cite>

## How it works

_keen.css_ provides three core algorithms – each covering specific aspects of design:

- `type`
- `layout`
- `skin`

### How to use the design system

Before you create your first design system with _keen.css_, take a look at how it will be used afterwards:

```html
<!DOCTYPE html>
<html keen-type keen-skin>
<head>
    <style>
        @import url("keencss/keen.css");
        /* Your unique design: */
        @import url("keencss/stdlib/layout.css");
        @import url("my-style/extends-keen.css");
    </style>
</head>
<body>
    <header>...</header>
    <nav>
        <ul keen-layout=flex>
            ...
        </ul>
    </nav>
    <main keen-type=pagecontent>
        <article>...</article>
    </main>
    <footer keen-skin=pagefooter keen-layout=grid-pad>
        <section>...</section>
        <section>...</section>
    </footer>
</body>
```

As you can see, _keen.css_ uses attributes instead of classes. The attribute marks the element from which the algorithm is applied. **The attribute value refers to the configured variant.** If a descendant element is marked with an algorithm attribute of the same type, the scope ends and the algorithm starts again with the specified configuration.

### How to create your own design system

> To be clear: **It's pure CSS.** You don't need any tools.

Copy or import _keen.css_ to the beginning of **your CSS file**.

```css
@import url("keencss/keen.css");

/* Your code here. */
```


#### Cascade layers to hook in

_keen.css_ declares [cascade layers](https://developer.mozilla.org/en-US/docs/Web/CSS/@layer) that you can hook into. For example, each algorithm has a `core` and a `lib` layer. There is also the `bootstrap` layer and the `postprocess` for the finishing touches.

> ℹ️ Tip: _keen_ has a **standard library** - in case you want to be even faster or looking for some inspiration. More on this in a chapter below.

#### Customize a core algorithm

To customize a base algorithm, **hook into the corresponding `core` layer**. In this example, the type algorithm is adjusted:

```css
/* my-style/extends-keen.css */

@layer keen.type.core {
    [keen-type] {
        --kt-font-size-base: clamp(1rem, 0.8913rem + 0.5435vw, 1.3125rem);
        --kt-scale-ratio: 1.25;
    }
}
```

#### Create a variant of a core algorithm

To create a variant, add it to the library. To do this, **hook into the corresponding `lib` layer**. To identify the variant, **give it a unique name**. In this example, the name is `pagecontent`.

```css
/* my-style/extends-keen.css */

@layer keen.type.lib {
    [keen-type|="pagecontent"] {
        --kt-font-size-base: calc(1em * var(--KT-SCALE-L));
        --kt-heading-font-family: serif;
        --kt-heading-5-font-family: inherit;
        --kt-heading-6-font-family: inherit;
    }
}
```

#### Standard Library 

The core of _keen.css_ is reduced to the essentials. This gives you a stable foundation and complete freedom for your ideas. But maybe you want to **skip all the construction work** and concentrate on your outstanding design features. In this case, the standard library offers you **a growing collection of algorithms** that you can easily adopt.

Copy or import the building blocks that fit into your design system idea. For example, a **responsive layout system**:

```css
@import url("keencss/keen.css");

/* Your selection from the Standard Library */
@import url("keencss/stdlib/layout.css");

/* Your own code here. */
```

#### 🎉 Congratulations

You have created the basis for **your own design system!**.

## Create something unique

I hope you got an idea how much _keen.css_ can speed up your design system development and free you to create something unique.

**If you have any questions or feedback**, feel free to open a new [discussion](https://github.com/keencss/keencss/discussions). 
