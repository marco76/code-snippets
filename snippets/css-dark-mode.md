In CSS is possible to change the style to dark mode if the user chose it.

CSS includes the (`preferes-color-scheme`)[https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme] feature that detect if the user chose the dark or light color scheme.

Here a code example:

```css
:root {
    --foreground: #111;
    --background: #f8f8f8;
}

@media (prefers-color-scheme: dark) {
    :root {
        --foreground: #f8f8f8;
        --background: #111;
    }
}

body {
    font-family: Arial, Helvetica, sans-serif;
    color: var(--foreground);
    background: var(--background);
}
```

``` javascript
const queue: number[] = [];
const QUEUE_MAX_LENGHT = 5;

this.queue.push(mmol);
if (this.queue.length > QUEUE_MAX_LENGTH) {
this.queue.shift();
}
```
