# Dev Notes

## From start to advanced.

## Disclaimer: this is going to be long!

## CSS Grid Terminology

- Grid Container: element with display property set to grid
- Grid Item: element that is direct descendant of the grid container
- Gride line: Horizontal (row) or Vertical (column) line separating the grid into sections
  - Are referenced by number 1 => n, respects the writing configuration (right to left or left to right), also can be named
- Grid cell: intersection between a grid row and a grid column --effectively, the same as a table cell
- Grid track: the space between two or more adjecent grid lines
  - Row tracks: horizontal
  - Column tracks: vertical
- Grid area: rectangular area between four specified grid lines
  - can cover one ore more cells
- Grid gap: the empty space between grid tracks, commonly called a gutters

## Grid Firefox tools

- Clicking on the grid icon adjacent to the container rule, we can see rules, layout and other visual aids to analize and project our grids

## grid-template-columns, grid-template-rows

[grid-template](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template)
[grid-template-columns](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns)
[grid-template-rows](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows)

## Fraction Unit (fr)

- Represents a fraction of the available space in the grid container

## Minmax function

[minmax](https://developer.mozilla.org/en-US/docs/Web/CSS/minmax)

- Defines a size range >= to min and <= to max
- example:

```css
grid-template-rows: 1fr minmax(10em, 20em) 1fr;
```

## repeat() Notation

[ref](https://developer.mozilla.org/en-US/docs/Web/CSS/repeat)

## Automatic placing

- By default the items inside a container are being positioned from top left to bottom right unless otherwise indicated

## Manual grid item placement

### grid-row and grid-column

- places the items delimited by the lines indicated
  - example:

```css
/* places the element from line 2 to line 4 in horizontal and from line 2 to line 3 in the vertical */
grid-column: 2/4;
grid-row: 2/3;
```

## Implicit lines

- If grid item placement requires additional columns or rows to be created, the browser adds implicit lines to keep the grid structurally sound.

## span Keyword

- The span keyword is used to define how many grid tracks an element should span.

## Named lines

- the name of the lines are wrapped by square brackets
- use hyphons and not spaces

```css
grid-template-columns: [left-edge] 2fr [middle-1] 1fr [middle-2] 1fr [right edge];
```

## Named lines shorthand

- If you are refering to the whole span between lines with the same prefix but different suffix (main-start vs. main-end), you can use the prefix without the suffix.
  -example:

  ```css
  grid-column: main-end/sidebar-end;
  /* is the same as */
  grid-column: main-end/sidebar;
  ```
