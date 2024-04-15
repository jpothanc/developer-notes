## Flex

Flexbox is a one-dimensional layout method for laying out items in rows or columns. Items flex to fill additional space and shrink to allow extra items.

### Flex Container Properties

- `display`: This defines a flex container. It can be `flex` or `inline-flex`.

- `flex-direction`: This defines the direction items are placed in the container. It can be `row`, `row-reverse`, `column`, or `column-reverse`.

- `flex-wrap`: By default, flex items will all try to fit onto one line. You can change that with `nowrap`, `wrap`, or `wrap-reverse`.

- `justify-content`: This defines the alignment along the main axis. It can be `flex-start`, `flex-end`, `center`, `space-between`, `space-around`, or `space-evenly`.

- `align-items`: This defines the default behavior for how items are laid out along the cross axis. It can be `stretch`, `flex-start`, `flex-end`, `center`, or `baseline`.

- `align-content`: This aligns a flex container's lines within the flex container when there is extra space in the cross-axis. It can be `stretch`, `flex-start`, `flex-end`, `center`, `space-between`, `space-around`, or `space-evenly`.

### Flex Item Properties

- `order`: By default, flex items are laid out in the source order. However, the `order` property can control the order in which they appear in the flex container.

- `flex-grow`: This defines the ability for a flex item to grow if necessary. It accepts a unitless value that serves as a proportion.

- `flex-shrink`: This defines the ability for a flex item to shrink if necessary.

- `flex-basis`: This defines the default size of an element before the remaining space is distributed.

- `align-self`: This allows the default alignment (or the one specified by `align-items`) to be overridden for individual flex items.

Please note that there are more properties available, but these are some of the basics to get you started.
