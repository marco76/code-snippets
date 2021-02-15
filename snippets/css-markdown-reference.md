
## Selectors

_[attribute^="text"]_

This selector select all the attributes starting with `text`.

This is particularly useful if you are using an external css that uses a prefix.

It can be used to apply a different style to internal and external links:

`a[href^="https://marco.dev"] {...}`

_[attribute$="text"]_

This selector select all the attributes ending with `text`.

`a[href$=".pdf"]::after { ... pdf icon ...}`

_[attribute*="text"]_

This selector select all the attributes containing `text`.

_[attribute~="text"]_

The partial looks for a partial match select all the attributes containing `text`.

_[attribute="text"]_

The selector select all the attributes with the following value `text`.

_[attribute]_

The selector select all the attributes with the following name `attribute`.

### :only selector

_:only-child_
Select only the child of an element

_:only-of-type_
Select only attributes that are children with the defined type.

`p:only-of-type` selects only `<p>` that are children of other elements.

### :child selector

_:first-child_
Apply the style to the first child of a series.

_:last-child_
Apply the style to the last child of a series.

_:first-of-type_
Apply the style to the first child of the defined type. A document can contain multiple of this attributes.

_:last-of-type_
Apply the style to the last child of the defined type. If the type is present only 1 time (first and last), it will be selected.
A document can contain multiple of this attributes.

_:nth-child()_
Apply the style to the element in the selected position.

`li:nth-child(even) {...}` applies the style to the elements in even position (2, 4, 6, ...)

`li:nth-child(odd) {...}` applies the style to the elements in odd position (1, 3, 5, ...)

`li:nth-child(4n + 2) {...}` applies the style to 2nd element and every 4th following

_:nth-last-child()_

Apply the style to the element in the selected position starting from the last.

### Pseudo-classes

_:checked_
It applies style when the property 'checked' is used in html (checkboxes and radiobuttons)

_:disabled_
It applies style when the property 'disabled' is used in html

_:enabled_
It applies style when the property 'disabled' is not used in html


_:required_
It applies style when the property 'required' is used in html

_:optional_
It applies the style when the property 'required' is not used in html

### target

_:target_ applies the style to the inside link cliked by the user
