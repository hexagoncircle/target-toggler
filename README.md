# `<target-toggler>`

A Web Component utility for toggling the visibility of another element on the page.

[Demo](https://hexagoncircle.github.io/target-toggler/demo.html)

## Why?

When toggling the display of some content, there are rare occasions that I want `<details>` element disclosure widget-style funtionality but with the `<summary>` element detached or living outside of its related `<details>` container. This Web Component enhances a `<button>` with the ability to toggle the contents of an element anywhere on a page.

## Usage

To get things working:

- Wrap any `<button>` with a `<target-toggler>`.
- Set a `target-id` attribute that matches the `id` of a page element.

```html
<script type="module" src="target-toggler.js"></script>

<target-toggler target-id="more-info">
  <button>Show more info</button>
</target-toggler>

<section>Some other content</section>

<section id="more-info">
  <!-- some good extra info -->
</section>
```

A `hidden` attribute will be added to that target element. When javascript is disabled, content will fallback to being visible, as the good web intended.

## Make content visible by default

Add a `target-visible` attribute and the targeted element will start off visible.

```html
<target-toggler target-id="more-info" target-visible>
  <button>Show more info</button>
</target-toggler>
```

## Display styles

The toggle button may not be necessary to show on screen since it does nothing without JS, so it can be hidden with CSS. I also prefer to set `display: contents` when the `<target-toggler>` element is defined so that it can rely on the display set for the `<button>` instead.

```css
target-toggler:not(:defined) {
  display: none;
}

target-toggler:defined {
  display: contents;
}
```

## Toggle styles

The `aria-expanded` attribute can be helpful for setting button styles when its respective content is visible. Here's an example that will flip an arrow icon, which can be seen in the [demo](https://hexagoncircle.github.io/target-toggler/demo.html):

```css
.button-with-icon[aria-expanded="true"] svg {
  transform: scaleY(-1);
}
```

## Improvements?

Please open a [new issue](https://github.com/hexagoncircle/target-toggler/issues/new) and share your ideas! I highly value any community feedback on how to improve this implementation.
