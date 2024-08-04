# Comprehensive CSS to Tailwind CSS Cheat Sheet

This cheat sheet offers a quick reference for converting standard CSS properties to their equivalent Tailwind CSS utility classes, categorized by functionality, with a focus on layout, typography, and visual effects.

## Layout Properties

### Display

| CSS Property | CSS Values                | Tailwind Utility            | Description                                  |
| ------------ | ------------------------- | --------------------------- | -------------------------------------------- |
| `display`    | `block`, `inline`, `none` | `block`, `inline`, `hidden` | Controls the display box type of an element. |

### Positioning

| CSS Property                     | CSS Values                                          | Tailwind Utility                                    | Description                                         |
| -------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- |
| `position`                       | `static`, `relative`, `absolute`, `fixed`, `sticky` | `static`, `relative`, `absolute`, `fixed`, `sticky` | Sets the type of positioning for an element.        |
| `top`, `right`, `bottom`, `left` | `<length>`, `<percentage>`, `auto`                  | `top-0`, `right-0`, `bottom-0`, `left-0`, etc.      | Sets the position of positioned elements.           |
| `z-index`                        | `<integer>`                                         | `z-0`, `z-10`, `z-20`, etc.                         | Controls the stacking order of positioned elements. |

## Typography and Text Styling

| CSS Property      | CSS Values                                                       | Tailwind Utility                                         | Description                                                      |
| ----------------- | ---------------------------------------------------------------- | -------------------------------------------------------- | ---------------------------------------------------------------- |
| `font-family`     | `<family-name>`, `<generic-family>`                              | Custom classes required                                  | Specifies the font for text.                                     |
| `font-size`       | `<absolute-size>`, `<relative-size>`, `<length>`, `<percentage>` | `text-xs`, `text-sm`, `text-lg`, etc.                    | Sets the size of the font.                                       |
| `font-weight`     | `normal`, `bold`, `bolder`, `lighter`, `<number>`                | `font-normal`, `font-bold`, `font-light`, etc.           | Sets the weight of the font.                                     |
| `text-align`      | `left`, `right`, `center`, `justify`                             | `text-left`, `text-right`, `text-center`, `text-justify` | Sets the horizontal alignment of the text.                       |
| `text-decoration` | `none`, `underline`, `overline`, `line-through`                  | `no-underline`, `underline`, `line-through`              | Specifies the decoration added to text.                          |
| `text-transform`  | `none`, `capitalize`, `uppercase`, `lowercase`                   | `normal-case`, `capitalize`, `uppercase`, `lowercase`    | Controls the capitalization of text.                             |
| `letter-spacing`  | `normal`, `<length>`                                             | `tracking-tighter`, `tracking-wide`, etc.                | Adjusts the spacing between characters in text.                  |
| `line-height`     | `normal`, `<number>`, `<length>`, `<percentage>`                 | `leading-none`, `leading-tight`, `leading-loose`, etc.   | Sets the line height to control the space between lines of text. |

## Box Model

| CSS Property      | CSS Values                         | Tailwind Utility                    | Description                                        |
| ----------------- | ---------------------------------- | ----------------------------------- | -------------------------------------------------- | --- | --------------- | ------------------------------------------------------- | ------------------------------------- |
| `width`, `height` | `<length>`, `<percentage>`, `auto` | `w-5`, `w-full`, `h-10`, `h-screen` | Sets the dimensions of an element.                 |
| `padding`         | `<length>`, `<percentage>`         | `p-0`, `p-4`, `p-8`, etc.           | Sets the padding space on all sides of an element. |
| `margin`          | `<length>`, `<percentage>`, `auto` | `m-0`, `m-4`, `m-auto`, etc.        | Sets the margin area around an element.            |
| `border`          | `<border-width>                    |                                     | <border-style>                                     |     | <border-color>` | `border`, `border-2`, `border-solid`, `border-gray-500` | Defines the border around an element. |

## Visual Effects

| CSS Property          | CSS Values                                                            | Tailwind Utility                                          | Description                                       |
| --------------------- | --------------------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------- |
| `background-color`    | `<color>`                                                             | `bg-red-500`, `bg-blue-100`, etc.                         | Sets the background color of an element.          |
| `background-image`    | `url()`, `none`                                                       | `bg-[url('/path/to/image')]`                              | Specifies an image as the background.             |
| `opacity`             | `<number>`                                                            | `opacity-50`, `opacity-75`                                | Sets the opacity level of an element.             |
| `box-shadow`          | `none`, `<h-offset> <v-offset> <blur-radius> <spread-radius> <color>` | `shadow`, `shadow-lg`                                     | Applies shadow effects around an element's frame. |
| `background-size`     | `auto`, `cover`, `contain`                                            | `bg-auto`, `bg-cover`, `bg-contain`                       | Specifies the size of the background image.       |
| `background-position` | `top`, `bottom`, `center`, `left`, `right`, `x% y%`                   | `bg-center`, `bg-top`, `bg-right`, etc.                   | Sets the starting position of a background image. |
| `background-repeat`   | `repeat`, `repeat-x`, `repeat-y`, `no-repeat`                         | `bg-repeat`, `bg-no-repeat`, `bg-repeat-x`, `bg-repeat-y` | Defines how the background image is repeated.     |

## Transitions and Animations

| CSS Property | CSS Values                                                                            | Tailwind Utility                                     | Description                                                              |
| ------------ | ------------------------------------------------------------------------------------- | ---------------------------------------------------- | ------------------------------------------------------------------------ |
| `transition` | `<property> <duration> <timing-function> <delay>`                                     | `transition`, `duration-300`, `ease-in`, `delay-150` | Allows CSS property changes to occur smoothly over a specified duration. |
| `animation`  | `<keyframes-name> <duration> <timing-function> <delay> <iteration-count> <direction>` | Custom utilities required                            | Connects animations to keyframes for describing the animation sequence.  |

This enhanced guide helps bridge the gap between traditional CSS and Tailwind CSS, offering a practical tool for web developers looking to optimize their workflow with comprehensive styling options.

## Flex Properties

| CSS Property                      | Tailwind Utility  | Description                                                                                    |
| --------------------------------- | ----------------- | ---------------------------------------------------------------------------------------------- |
| `display: flex;`                  | `flex`            | Defines a flex container.                                                                      |
| `flex-direction: row;`            | `flex-row`        | Items are placed in a row.                                                                     |
| `flex-direction: column;`         | `flex-col`        | Items are placed in a column.                                                                  |
| `flex-wrap: wrap;`                | `flex-wrap`       | Items will wrap onto multiple lines.                                                           |
| `flex-wrap: nowrap;`              | `flex-nowrap`     | Items will not wrap.                                                                           |
| `justify-content: flex-start;`    | `justify-start`   | Items are aligned to the start of the container.                                               |
| `justify-content: flex-end;`      | `justify-end`     | Items are aligned to the end of the container.                                                 |
| `justify-content: center;`        | `justify-center`  | Items are centered in the container.                                                           |
| `justify-content: space-between;` | `justify-between` | Items are distributed with space between them.                                                 |
| `justify-content: space-around;`  | `justify-around`  | Items are distributed with space around them.                                                  |
| `justify-content: space-evenly;`  | `justify-evenly`  | Items are evenly distributed in the container.                                                 |
| `align-items: flex-start;`        | `items-start`     | Items are aligned to the start of the cross axis.                                              |
| `align-items: flex-end;`          | `items-end`       | Items are aligned to the end of the cross axis.                                                |
| `align-items: center;`            | `items-center`    | Items are centered along the cross axis.                                                       |
| `align-items: baseline;`          | `items-baseline`  | Items are aligned such as their baselines align.                                               |
| `align-items: stretch;`           | `items-stretch`   | Items are stretched to fit the container.                                                      |
| `align-content: flex-start;`      | `content-start`   | Lines are packed to the start of the container.                                                |
| `align-content: flex-end;`        | `content-end`     | Lines are packed to the end of the container.                                                  |
| `align-content: center;`          | `content-center`  | Lines are centered in the container.                                                           |
| `align-content: space-between;`   | `content-between` | Lines are evenly spaced; first line is at the start of the container and last line at the end. |
| `align-content: space-around;`    | `content-around`  | Lines are evenly spaced, with equal space around them.                                         |
| `align-content: stretch;`         | `content-stretch` | Lines stretch to take up the remaining space.                                                  |

## Item Properties

| CSS Property              | Tailwind Utility                    | Description                                            |
| ------------------------- | ----------------------------------- | ------------------------------------------------------ |
| `align-self: auto;`       | `self-auto`                         | Inherits the container's `align-items` property.       |
| `align-self: flex-start;` | `self-start`                        | Aligns the item to the start of the cross axis.        |
| `align-self: flex-end;`   | `self-end`                          | Aligns the item to the end of the cross axis.          |
| `align-self: center;`     | `self-center`                       | Centers the item along the cross axis.                 |
| `align-self: baseline;`   | `self-baseline`                     | Aligns the item along its baseline.                    |
| `align-self: stretch;`    | `self-stretch`                      | Stretches the item to fill the container (cross-axis). |
| `flex-grow: 0;`           | `flex-grow-0`                       | The item will not grow.                                |
| `flex-grow: 1;`           | `flex-grow`                         | The item will grow to fill available space.            |
| `flex-shrink: 0;`         | `flex-shrink-0`                     | The item will not shrink.                              |
| `flex-shrink: 1;`         | `flex-shrink`                       | The item will shrink if necessary.                     |
| `flex-basis: {value};`    | `basis-{value}` (e.g., `basis-1/4`) | Specifies the initial size of the item.                |

These Tailwind utilities allow you to control the layout of flex containers and items directly within your HTML, maintaining a cleaner and more maintainable codebase.
