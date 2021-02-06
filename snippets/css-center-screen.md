In CSS you can create a container that center the content in the screen.

### Using a grid

This strategy uses a grid that has the size of the full screen and cented his items.

Here the snippet

```css
.container-center-wrapper {
  display: grid;
  grid-template-columns: 1fr; /* Fr is a 'fractional unit', 1fr represents 1 part of the available space */
  grid-template-rows: 100vh; /* vh: 1% of the height of the viewport, 100vh represents the size of the viewport */
  align-items: center; /* Center the alignments for all the items of the flexible <div> element */
  justify-items: center;
}
```

```html
<div class="container-center-wrapper">
  <div> <!-- this content is centered in the screen -->
  </div>
</div>
```

_Reference_

(Mozilla documentation: Aligning Items in a Flex Container)[https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Aligning_Items_in_a_Flex_Container]