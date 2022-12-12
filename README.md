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

## Grid Areas

### grid-template-areas

[ref](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-areas)

- it is applied to a grid container
- uses a text-based grid map to apply grid area neames to individual cells

- First we "paint" our layout with text, giving names to each area using the property grid-template-areas
  -example:

  ```css
  grid-template-areas:
    "title title title"
    "main masthead masthead"
    "main sidebar footer";
  ```

  - Then we assign the area for each element in the css rules using the property grid-area
    [grid area ref](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-area)

  ```css
  .masthead {
    grid-area: masthead;
  }
  ```

## Grid gap (alias for gap)

[ref](https://developer.mozilla.org/en-US/docs/Web/CSS/gap)

" So in short, grid-gap creates space between each column or row inside your layouts, while at the same time respecting any item that spans across multiple rows, multiple columns, or is displayed inside a grid area. "

## Planning For Grid Layouts

### CSS Grid Means Rethinking Web Layouts

" Using CSS Grid introduces a whole new approach to web layouts and web design. We are now working from the outside in. Start with a grid, then place our contents on that grid. This in turn requires us to think carefully about the relationships between different items of content, both from an HTML semantics perspective, from a communication perspective, and from a layout and design perspective. "

### CSS Grid Features: Grid Items

- Only direct first-level descendants of the grid container
- Second level descendatns need their own grid
- Subgrids are not supported
- Don't flatten your HTML, rather embrace Nested Grids

### CSS Grid Features: True Grid

- Avoid Masonry styles
- Think in tracks and then place the elements in it

### CSS Grid Features: Grid Stacking

- Elements can be placed anywhere in the grid including placing one item on top of another
- Items are stacked according to the HTML source order
- Items can be reordered using the z-index property

### CSS Grid Features: Content Order

- Manual placement is not impacted by the source order
- Make sure the visible content order matches the source content order to preserve mainingful communication

### CSS Grid Features: Pure CSS Grids

- Grids are defined using pure CSS
- Grids can be nested inside media queries
- Grids can be applied conditionally
- Grids can be added, changes, or removed without affecting the HTML

## Start your Layouts with pen and paper

1. Make mobile-first layouts drafts to map out the relationships between items
2. Draw grid lines to identify columns, rows, cells and grid areas
3. Break grid apart to identify where nesting is needed
4. Repeat the process for each content model/view

## Backward Compatibility Options

- Build full-fledged fallbacks for all browsers
- Use a mobile-first layout for all browsers
- Use CSS Grid and rely on block-level fallbacks

## Accessibility First

- CSS Grid allows us to simplify HTM by reducing container nesting and separating semantic order from displayed order
- Changing the displayed order of contents can change their meaning, so use this feature with care

=> make it accesible first, then fancy, then make sure that fancy doesn't break accessibility <=

## Using white space to perform magic

- We have a sidebar with two parts belonging to a specific grid item
- What if we want to separate those two parts and in certain viewport widths, place one at each side?
- The answer is: we make the sidebar a grid container (with inheritance)
- then make the sidebar span the original width
- To solve the issue of empty space between sidebar sections in opposite sides: set the height of the new grid item. Exploit the way the browser bahaves, set height of the new grid container (sidebar) to be 0 height and let the browser show it because we haven't set a rul to overflow hidden.

## Full-Bleed Single Column Layout

### What is the Challenge?

The full-bleed single column layout features sections and images that span the full width of the view port, thereof full-bleed, and the contents within each section are center-aligned with a max width. Doing this without CSS Grid requires a lot of extra container nesting and can be quite messy on the HTML site.

Technically what we're looking for in this layout is a four-column grid where full-bleed content takes up all four columns and the centered content takes up the two middle columns. The problem is, we can't use a single global grid to do this because the grid items would be the individual sections and we would have no way of aligning the contents within those sections to the grid. So, what do we do? The solution is to apply the same grid to each section, effectively making a list of matching grids. That way we can align the contents within each section to the grid since they are grid items, while at the same time controlling the overall layout because all the grids are controlled using the same CSS rule.

## Card Layouts

Preserve the visual consistency even if they display different content

### Text-based cards

- starting with a full bleed card layout as fallback

### super-imposed text cards / image based cards

[figure element reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/figure)

### advance card layout
