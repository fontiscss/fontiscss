# ⛲ fontis.css

**The _Algorithmic CSS_ Framework**

> _fontis_ is not like other CSS frameworks. CSS is a programming language and _fontis.css_ activates its power to help you and your team develop unique design systems faster.  
<cite>[David J. Schwarz](https://davidschwarz.eu/)</cite>

## Understand it by example:

Start with _your_ CSS file:

```css
/* fontis.css has its own layers, so you can just import it. */
@import url("fontis.css");

/* Adopt the typography algorithm ... */
[data-typography|="myStyle"] {

    /* ... and adjust the parameters according to your needs. */
    /* For example, the ratio of the type scale: */
    --font-scale-ratio: calc(5 / 4);
}

/* And create as many flavors as you like. */
[data-typography="myStyle-mainContent"] {

    /* Change the font size of paragraphs from which the other sizes are calculated. */
    --font-size-base: 1.2rem;
}
```

Now go to your HTML file:

```html
<!-- Specify the scope in which the respective typography algorithm is to be applied. -->
<body data-typography=myStyle >
    <header> ... </header>
    <main data-typography=myStyle-mainContent > ... </main>
    <footer> ... </footer>
</body>
```
__Look at the magic.__ Open your page in the browser. The font sizes of _all headings and content are in harmony_ with each other. 🎉

### another category of algorithms

You probably noticed that all the spaces between the blocks have disappeared. Spaces in between are the task of another category of algorithms: **layout algorithms**. A simple example:

```html
<article data-layout=flow >
```
Try it - that's all it takes to place the blocks (headings, paragraphs, etc.) in an article in a meaningful way.

**But you might want to have more control** over what spacing a `<h2>` has, for example. No problem! Go back to your CSS to do this.

```css
[data-typography|="myStyle"] {
    --font-scale-ratio: calc(5 / 4);

    /* Expand your typography algorithm: */

    & h2 {
        --flow-space: calc(var(--SEM) * 2);
    }
    & h1 + h2 {
        --flow-space: var(--SEM);
    }
}
```

What is happening here? You see two useful custom properties `--flow-space` and `--SEM`.  
First to `--flow-space`: With `--flow-space` you make a _concrete suggestion_ to the layout algorithm which length can be taken for the spacing of `<h2>`.  
`sem` stands for "scope em" - a unit calculated by _fontis.css_, which refers to the base font size of the typography scope. `--SEM` equals `1sem` (and is in upper case, because its value should not be changed by you). Yes, you read correctly: **_fontis.css_ has a "scoped rem"**. This allows lengths to scale with the text.

I hope you got an idea how much _fontis.css_ can speed up your design system development and free you to create something unique.

> To be clear: **It's pure CSS.** You don't need any tools.

**Try this early version of ⛲ _fontis.css_ and share your experience.**
